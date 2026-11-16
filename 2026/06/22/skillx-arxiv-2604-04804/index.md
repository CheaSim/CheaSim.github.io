# SkillX：给 Agent 预先造一个可复用技能库

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2026/06/22/skillx-arxiv-2604-04804/
发布日期：2026-06-22
更新日期：2026-06-22
标签：LLM、Agent、Skill、Memory、Planning

从历史轨迹中提炼多层技能，梳理 SkillX 自动构建、修订与扩展 Agent 技能知识库的方法。



## 讨论的原论文与代码

- 原论文：https://doi.org/10.48550/arXiv.2604.04804
- PDF：https://arxiv.org/pdf/2604.04804
- Code：https://github.com/zjunlp/SkillX
- 来源：arXiv · 预印本（Work in progress） · 原论文

本文是个人论文导读，请区分博客解读和原论文结论；不要据此推断博主是原论文作者。

昨天写了 [SGA-MCTS](https://www.cheasim.com/2026/06/21/sga-mcts-arxiv-2604-14712/)，今天顺手接一篇很适合放在一起看的论文：[SkillX: Automatically Constructing Skill Knowledge Bases for Agents](https://arxiv.org/abs/2604.04804)。

SGA-MCTS 更像是在说：Agent 的搜索经验能不能拆成可检索的规划原子。SkillX 则更进一步问：能不能自动把 Agent 的历史轨迹整理成一个 plug-and-play 的技能知识库，让别的 Agent 也能直接拿来用？

这个方向我觉得很有意思，因为它开始把 Agent 的能力建设从“单个模型临场发挥”，推向“系统性沉淀经验”。

## 问题在哪里

现在很多 self-evolving Agent 的套路是：让 Agent 自己跑任务、总结失败、改进策略，然后下一次做得更好。

听起来很自然，但问题也很明显：

- 每个 Agent 都在自己的小世界里学习；
- 很多相似行为会被反复探索；
- 强模型跑出来的经验，很难直接转给弱模型；
- 原始轨迹太长、太乱，不适合作为稳定能力复用。

SkillX 的出发点就是解决这个浪费：不要让每个 Agent 都从头摸索同样的东西，而是预先构建一个结构化技能库，让经验变成可迁移的资产。

## SkillX 做了什么

论文提出的是一个全自动 pipeline，用强 Agent 先在训练任务上 rollout，拿到成功轨迹，再把这些轨迹蒸馏成技能库。

它的核心不是把轨迹原封不动存起来，而是做三层技能抽象：

```text
Planning Skills: 高层任务组织和策略规划
Functional Skills: 可复用的工具型子流程
Atomic Skills: 具体执行时的工具调用模式和约束
```

这三层划分挺关键。因为 Agent 的经验并不是单一粒度的东西：有些经验是“先拆任务再查证据”的高层策略，有些经验是“如何组合多个工具完成一个子任务”，还有些经验只是“调用某个 API 时参数应该怎么填”。

如果全都塞成一段自然语言反思，检索和复用都会很糙；如果拆得太细，又容易丢掉上下文。SkillX 的三层设计就是想在这之间找一个更稳的结构。

## 三个模块

SkillX 主要靠三个机制把技能库做起来。

第一是 Multi-Level Skills Design。它把成功轨迹整理成 planning、functional、atomic 三个层级，避免只存原始 workflow 或者一段笼统 reflection。

第二是 Iterative Skills Refinement。技能不是抽出来就完事，而是根据执行反馈不断合并、过滤、修订。这个点很重要，因为自动提取出来的技能一定会有噪声：有些太具体，有些不完整，有些只是偶然成功。

第三是 Exploratory Skills Expansion。它会主动围绕未充分使用的工具、容易失败的行为去扩展技能覆盖，而不是只依赖初始训练数据里碰巧出现过的轨迹。

所以 SkillX 不是一个静态笔记本，更像是一个会被持续打磨的技能仓库。

## 为什么它不是普通 memory

很多 Agent memory 会存历史对话、任务轨迹、失败总结，下一次靠检索塞回上下文。

SkillX 的区别在于，它更强调“技能”这个中间表示：不是存发生过什么，而是存以后还能怎么做。

可以粗略这样分：

```text
Raw trajectory: 我当时做了什么
Reflection: 我当时为什么错了
Skill: 下次遇到类似结构时应该怎么做
```

这也是 SkillX 和昨天那篇 SGA-MCTS 能接上的地方。SGA-MCTS 把规划搜索结果拆成 State-Goal-Action 原子，SkillX 把成功轨迹拆成多层技能。两者都在绕开一个问题：不要每次都把所有推理压给在线上下文。

## 一个直觉例子

假设 Agent 要完成一个“查订单、判断退款条件、给用户回复”的任务。

原始轨迹可能很长：

1. 打开订单系统；
2. 查用户 ID；
3. 找订单状态；
4. 查支付时间；
5. 打开退款政策；
6. 对照退款窗口；
7. 生成回复。

SkillX 希望把它抽成不同层级的技能：

```text
Planning Skill: 先收集订单事实，再对照政策条件，最后生成可解释回复
Functional Skill: 查询订单状态和支付时间
Atomic Skill: 调用订单查询接口时必须同时传入 user_id 和 order_id
```

这样下次换一个任务，哪怕不是退款，而是改签、赔付、取消订阅，只要结构相似，某些技能仍然可以复用。

## 实验里值得注意的点

论文使用 GLM-4.6 作为强 backbone agent 预先构建技能库，然后把这个 SkillKB 插到较弱的 base agents 上，比如 Qwen3-32B。

评测任务包括 AppWorld、BFCL-v3 和 $\tau^2$-Bench，都是偏长程、交互式、工具调用密集的 Agent benchmark。论文报告说，这种 plug-and-play 的技能库能带来大约 10% 的性能提升，同时改善执行效率。

这里我最关心的不是那个具体数字，而是这个实验设定本身：强 Agent 生产结构化经验，弱 Agent 消费经验。这其实很像一种“能力蒸馏”，但蒸馏的对象不是模型参数，而是外部技能知识库。

## 我比较喜欢的点

SkillX 的工程味很重。它没有假设每次都要重新训练模型，也没有只靠 prompt 里塞一大段历史经验，而是把 Agent 经验做成一个可管理、可检索、可迭代的外部系统。

这对真实 Agent 产品挺关键。因为线上系统最怕的是：

- 每次任务都重新探索；
- 经验只能留在单次上下文里；
- prompt 越堆越长；
- 失败修复没有结构化入口。

如果技能库真的能持续积累，那 Agent 的进步就不只是“模型版本升级”，还可以是“组织经验变厚”。

## 还需要追的问题

这类方法我会继续看几个风险点：

- 自动抽取出来的技能到底有多少是稳定可迁移的；
- 技能库大了以后，检索错技能会不会带来负迁移；
- planning / functional / atomic 三层边界是否清晰；
- 不同环境里的工具接口变化，会不会让技能快速过期；
- 技能的安全性和权限边界怎么管理。

尤其是最后一点。一个技能库如果能被多个 Agent 复用，它就不只是提示词资产，也可能变成系统行为的一部分。技能写错、过期、权限过大，都会影响执行。

## 先记到这里

SkillX 和 SGA-MCTS 这两篇放在一起看，会看到一个很明显的趋势：Agent 不应该只靠在线推理“现想现做”，而应该把成功经验、搜索结果、工具使用模式系统性沉淀下来。

未来 Agent 系统里，模型本身当然重要，但模型外面的经验层、技能层、检索层，可能也会越来越像一等公民。

这也是我最近比较想追的一条线：Agent 的能力到底应该存在参数里，还是存在一个可维护的外部技能系统里？



## 原论文 BibTeX

```bibtex
@misc{a22026,
  title = {SkillX: Automatically Constructing Skill Knowledge Bases for Agents},
  author = {Chenxi Wang and Zhuoyun Yu and Xin Xie and Wuguannan Yao and Runnan Fang and Shuofei Qiao and Kexin Cao and Guozhou Zheng and Xiang Qi and Peng Zhang and Shumin Deng},
  year = {2026},
  howpublished = {arXiv · 预印本（Work in progress）},
  url = {https://doi.org/10.48550/arXiv.2604.04804}
}
```


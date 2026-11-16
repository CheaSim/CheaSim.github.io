# Skill0：训练时借技能，推理时把技能撤掉

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2026/06/24/skill0-arxiv-2604-02268/
发布日期：2026-06-24
更新日期：2026-11-16
标签：LLM、Agent、Skill、RL、Planning

外部技能库能否只在训练时使用？从 Skill0 看 Agent 如何把经验内化到模型参数中。

> 把技能当作训练时的脚手架，而不是推理时永远依赖的提示。

## 摘要

本文梳理 SKILL0 如何在训练早期提供外部技能，再逐步减少技能上下文，让 Agent 在无运行时技能检索的条件下执行任务。重点讨论动态课程与技能内化的关系，并用明确标注的概念示例解释预算撤除；示例不等同于原论文实现。

## 讨论的原论文与代码

- 原论文：https://arxiv.org/abs/2604.02268
- PDF：https://arxiv.org/pdf/2604.02268
- Code：https://github.com/ZJU-REAL/SkillZero
- 来源：arXiv 2026 · 论文导读

本文是个人论文导读，请区分博客解读和原论文结论；不要据此推断博主是原论文作者。

前两篇刚好写了 [SGA-MCTS](https://www.cheasim.com/2026/06/21/sga-mcts-arxiv-2604-14712/) 和 [SkillX](https://www.cheasim.com/2026/06/22/skillx-arxiv-2604-04804/)，今天这篇 [SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization](https://arxiv.org/abs/2604.02268) 正好能把这条线补完整。

如果说 SGA-MCTS 和 SkillX 都是在讨论“怎么把 Agent 经验放到外部系统里”，那 Skill0 问的是另一个更狠的问题：外部技能库能不能只在训练时用，最后把技能内化到模型参数里，让 Agent 测试时不再依赖 runtime skill retrieval？

一句话概括：训练时给模型看技能，随着 RL 训练逐步把技能撤掉，逼模型从“照着技能做”变成“自己会做”。

## 为什么要把技能撤掉

本文讨论的原始工作见 [1](https://arxiv.org/abs/2604.02268)。（旁注：这里的“技能内化”指训练目标，不意味着外部技能库在所有工程场景中都应被移除。）

现在很多 Agent 系统会在推理时加载技能：先检索相关 skill file，再把技能内容塞进上下文，让模型照着做。

这条路线很实用，但论文指出它有几个天然问题：

- 检索会有噪声，可能捞到不相关甚至误导性的技能；
- 技能内容会占上下文，长任务里 token 开销很明显；
- 模型只是临时 follow skill，并没有真正学会这个技能；
- 一旦检索失败，Agent 的行为就容易退化。

所以 Skill0 的目标不是再做一个更好的 skill retriever，而是把 skill 当成训练时的脚手架。脚手架搭模型，最后脚手架要拆掉。

这个思路我挺喜欢，因为它把“技能库”和“参数学习”连接起来了：技能库不是最终形态，而是训练模型的中间媒介。

## Skill0 的核心想法

Skill0 是一个 in-context agentic reinforcement learning 框架。它训练时不是一上来就让模型裸跑，而是给模型完整技能上下文，让它先在有提示的状态下学会工具调用、多轮交互和任务完成。

然后关键来了：训练过程中逐步减少可用技能上下文。

可以粗略理解成一个 curriculum：

```text
early training: 给完整技能，模型先照着做
middle training: 只保留仍然有帮助的技能
late training: 技能预算继续下降
final policy: 不再加载技能，零样本执行
```

这种设计像是“先扶着走，再逐渐放手”。如果直接不给技能，RL 探索太难；如果一直给技能，模型永远只是依赖外部提示。Skill0 想在这两者之间找一条退火路径。

## Dynamic Curriculum

论文里最关键的机制是 Dynamic Curriculum。它不是机械地每隔几步删掉一些技能，而是根据当前 policy 的 on-policy helpfulness 来决定哪些 skill file 还值得保留。

也就是说，一个技能如果当前模型还明显受益，就暂时留着；如果模型已经不太需要它，或者它帮助不大，就可以从上下文预算里撤掉。

同时，总技能预算会线性下降，最后逼近零。

这个机制背后的直觉很清楚：不同技能被模型吸收的速度不一样。有些简单工具调用模式很快就会了，有些长程规划技巧需要保留更久。动态课程比固定删减更像真实教学。

## 为什么叫 in-context RL

Skill0 里技能仍然是通过上下文注入的，但它的目标不是长期依赖上下文，而是借助上下文提高 RL 采样质量。

普通 RL baseline 里，模型需要自己探索出好行为。Agent 任务通常奖励稀疏、步骤长、工具调用容易错，探索成本很高。

Skill0 则让模型在训练早期拥有更强的行为先验：

```text
skill context -> better trajectories -> better RL signal -> policy internalization
```

这里的 in-context 更像训练时的辅助观测。它让模型更容易走到成功轨迹，再通过 RL 把这些行为模式压进参数里。

## 和 SkillX 的关系

SkillX 是自动构建技能知识库，让弱 Agent 可以 plug-and-play 地消费强 Agent 的经验。

Skill0 则像是下一步：既然有了技能库，能不能不在推理时每次都检索，而是在训练时把技能喂给模型，让模型最后自己会？

所以可以把两篇放在一条链上看：

```text
SkillX: 经验 -> 技能库
Skill0: 技能库 -> 参数化能力
```

这条链很有想象力。因为真实系统里，外部技能库和模型参数不是非此即彼。技能库可以用来冷启动、训练、纠错、更新；参数化能力则负责低延迟、低 token 成本、稳定执行。

## 实验结果怎么读

论文在 ALFWorld、Search-QA、WebShop 这类 Agent benchmark 上做实验，报告相对标准 RL baseline 有明显提升：

- ALFWorld：约 +9.7%
- Search-QA：约 +6.6%
- WebShop：约 +10.1%

同时，它每步上下文控制在 0.5k tokens 以下。这个点很关键，因为如果一个方法靠堆很长的 skill context 获得提升，线上成本会很难看。Skill0 的卖点正好相反：训练时用技能，最后尽量把 runtime 负担降下来。

当然，这些数字还要看 benchmark 细节和 baseline 设置。但方向本身很清晰：技能上下文可以成为 RL 的辅助训练信号，而不一定是推理阶段永久依赖项。

## 一个直觉例子

假设一个 WebShop Agent 要学会买商品。外部技能可能会告诉它：

```text
先解析用户需求
再搜索候选商品
过滤价格、颜色、尺寸等约束
最后打开详情页确认再购买
```

如果推理时每次都把这段技能塞进去，模型可以照做，但会有 token 成本，也可能检索到不合适的购买策略。

Skill0 的路线是：训练早期把这段技能给模型，让它更容易跑出成功购买轨迹。训练中后期逐渐减少提示，让模型自己学会“先检索、再过滤、再验证”的流程。最终上线时，不再需要把这段技能塞进 prompt。

这个思路非常像工程里的知识蒸馏，只是蒸馏对象不是 logits，而是 Agent 行为策略。

## 我比较喜欢的点

Skill0 的价值不只是“又一个 RL trick”，而是它提出了一种很实用的 Agent 能力迁移方式：

- 外部技能库负责提供结构化先验；
- RL 负责把先验转成可执行策略；
- curriculum 负责逐步减少依赖；
- 最终模型负责低开销执行。

它也回答了一个很现实的问题：如果我们真的维护了很多 skill file，难道每次推理都要检索、拼 prompt、赌模型 follow 对吗？

Skill0 给出的答案是：不一定。技能可以是训练材料，不一定永远是运行时依赖。

## 还需要追的问题

这类方法后面我会继续关注几个点：

- 技能内化后，模型是否真的学会了可迁移策略，还是只记住了 benchmark 模式；
- 训练时撤掉技能的节奏对最终效果有多敏感；
- 如果技能库里有错误技能，RL 会不会把错误行为也内化进去；
- 新工具、新环境出现时，已经内化的技能如何更新；
- 参数化技能和外部技能库应该怎么协同，而不是互相替代。

最后一点尤其重要。外部技能库的优点是可编辑、可审计、更新快；参数化技能的优点是低延迟、低 token、行为稳定。真实 Agent 系统大概率需要两者都要。

## 小结

SGA-MCTS、SkillX、Skill0 这三篇放在一起看，会形成一条很自然的路线：

```text
先把搜索经验变成可检索原子
再把轨迹经验变成技能知识库
最后把技能逐步内化进模型参数
```

这也许是 Agent 系统接下来很重要的一条工程路线：不是只靠更大的模型，也不是只靠更长的 prompt，而是让经验在外部系统和模型参数之间流动起来。

我觉得这个方向值得继续追。Agent 真正变强，可能不只是因为它“想得更久”，而是因为它开始有办法把过去想过、做过、错过的东西沉淀下来。

## 补记：把“撤掉脚手架”画出来

下面是为了帮助理解而画的概念图与简化预算示例，**不是论文的算法复现或实验结果**。[^budget-note]

![外部技能经训练轨迹影响模型参数的概念流程](https://www.cheasim.com/images/skill-learning-flow.svg "从外部提示到参数学习：本文绘制的概念示意。")

[图 1](https://www.cheasim.com/2026/06/24/skill0-arxiv-2604-02268/#figure-1) 用来帮助理解经验流动；[表 1](https://www.cheasim.com/2026/06/24/skill0-arxiv-2604-02268/#table-1) 给出下面这个简化预算模型的数值示例。

### 一个最简单的预算模型

把初始预算记为 $B_0$，训练步记为 $t$，总步数为 $T>0$，线性撤除的直觉可写成：

$$
B(t)=B_0\max\left(0,1-\frac{t}{T}\right)
\tag{1}
$$

```python {filename="budget_example.py"}
def skill_budget(step: int, total_steps: int, initial: int) -> int:
    if total_steps <= 0:
        raise ValueError("total_steps must be positive")
    fraction = max(0.0, min(1.0, step / total_steps))
    return round(initial * (1.0 - fraction))
```

| 阶段 | 示例步数 $t/T$ | 剩余预算 | 应当关注的问题 |
|:---|---:|---:|:---|
| 早期 | 0 | $B_0$ | 技能是否帮助探索？ |
| 中期 | 0.5 | $0.5B_0$ | 减少提示后是否仍能完成任务？ |
| 结束 | 1 | 0 | 无提示评估是否稳定？ |
{caption="线性预算撤除的概念示例，不代表论文实验结果"}

#### 阅读时的小提醒

> [!NOTE]
> 表格只是上面公式的算术示例，不提供任何性能结论。

> [!TIP]
> 比较结果前，先核对训练预算和评估设置是否一致。

> [!WARNING]
> 线性预算不能替代前文讨论的动态课程。

> [!DANGER]
> 如果把测试答案混入技能提示，评估会失去意义。

> 技能可以是训练材料，不一定永远是运行时依赖。
{.pull-quote}

<mark>无提示评估</mark>是这份阅读清单里最想继续追的一项：

- 训练条件
  - 技能来源是否清楚；
  - 预算变化是否可复现。
- 评估条件
  1. 对齐任务与奖励；
  2. 区分训练辅助与测试输入。

- [x] 区分概念示意与论文结果。
- [ ] 继续核对动态课程的实现细节。

[^budget-note]: 公式与代码由本文补充，仅用于解释预算逐步降低的直觉；论文方法请以文首原始链接为准。


## 参考文献

1. Zhengxi Lu, Zhiyuan Yao, Jinyang Wu, Chengcheng Han, Qi Gu, Xunliang Cai, Weiming Lu, Jun Xiao, Yueting Zhuang, Yongliang Shen. [SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization](https://arxiv.org/abs/2604.02268) (2026).

## 原论文 BibTeX

```bibtex
@misc{lu2026skill0,
  title = {SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization},
  author = {Zhengxi Lu and Zhiyuan Yao and Jinyang Wu and Chengcheng Han and Qi Gu and Xunliang Cai and Weiming Lu and Jun Xiao and Yueting Zhuang and Yongliang Shen},
  year = {2026},
  eprint = {2604.02268},
  archivePrefix = {arXiv},
  url = {https://arxiv.org/abs/2604.02268}
}
```


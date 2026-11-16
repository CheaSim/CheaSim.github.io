# 如何在colab用pytorch_lightning白嫖TPU

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2021/01/07/%E5%A6%82%E4%BD%95%E5%9C%A8colab%E7%94%A8pytorch-lightning%E7%99%BD%E5%AB%96tpu/
发布日期：2021-01-07
更新日期：2021-01-07





# 如何在colab用pytorch_lightning白嫖TPU

## 首先

我们得熟悉pytorch_lightning以及colab的操作。在使用TPU之前，先挂载好我们的云端磁盘以及配置好pytorch需要的TPU环境。

```python
from
drive.mount('/content/gdrive'
import
os.chdir("gdrive/MyDrive/path_to_your_file"
! pip install pytorch_lightning

# 试图使用TPU
!curl https://raw.githubusercontent.com/pytorch/xla/master/contrib/scripts/env-setup.py -o pytorch-xla-env-setup.py
!python pytorch-xla-env-setup.py  --apt-packages libomp5 libopenblas-dev
```

安装好pytorch_lightning以及配置好环境之后，我们就可以开始在pytorch_lightning框架下跟写GPU代码一样写TPU代码。下面请看VCR，一个小栗子。

如何在colab用pytorch_lightning白嫖TPU

https://www.cheasim.com/uncategorized/2021/01/07/%E5%A6%82%E4%BD%95%E5%9C%A8colab%E7%94%A8pytorch-lightning%E7%99%BD%E5%AB%96TPU.html

作者
CheaSim

发布于
2021-01-07

更新于
2021-03-08

许可协议

#[colab](https://www.cheasim.com/tags/colab/)[小技巧](https://www.cheasim.com/tags/%E5%B0%8F%E6%8A%80%E5%B7%A7/)





---
layout: intro
class: text-center
highlighter: shiki
download: >-
  https://raw.githubusercontent.com/jindaliuzi444/jindaliuzi444.github.io/master/slides-export.pdf
info: |
  # 论文分享

  分布式训练深度强化学习调度算法

  [范也]() at [Oct 27th 2021]()
title: 进度报告 论文分享
---

# 进度报告&论文分享

DRL与元学习、分布式相结合

范也 2021.10.27


---
layout: two-cols
---

::default::

# 研究进度

1. 使用ddpg，效果不好
2. 换成discrete的D3QN算法，勉强可以

![](/img/d3qn.png)

::right::

# 后续

1. 加入网络传输延迟
2. 设计公式、数据
3. 尝试与分布式、元学习等结合


---

## Fast Adaptive Task Offloading in Edge Computing based on Meta Reinforcement Learning

期刊：TPDS 2021 Jan

作者：Jin Wang, Jia Hu, Geyong Min, Albert Y. Zomaya

机构：University of Exeter, United Kingdom.

<div style="width:500px">

### 摘要：
训练drl算法需要的时间比较长，对于不同的环境还需要分别训练。
1. 使用meta-rl的方法，仅需较少次数的更新，便可以适应新的环境。
2. 使用seq2seq编码DAG，最小化延迟，快速适应新的环境。

</div>

---

# 架构

<div></div>

![](/img/fast_arch.png)


---
layout: two-cols
---

::default::

# 网络

<div></div>
<br/>
<br/>

<img src="/img/fast_net.png" width="380"/>
<br/>

- encoder: task embeddings
- decoder: offloading decisions, value function

::right::

# 训练
<div></div>

1. inner loop：使用meta-policy初始化本地网络，在本地抽样训练
2. outer loop：使用本地的参数更新meta-policy

---

# 元强化学习 (Meta Reinforcement Learning)

<div></div>

![](/img/fast.png)

---

# 实验
<div></div>

![](/img/fast_table.png)

<img src="/img/fast_eva.png" width="900" />

---

## Distributed and Collective Deep Reinforcement Learning for Computation Offloading: A Practical Perspective

期刊：TPDS 2021 May

作者：Xiaoyu Qiu, Weikun Zhang, Wuhui Chen,  Zibin Zheng

机构：中山大学

## 摘要

1. 使用分布式、协同方法训练，增多数据量，提升泛化性
2. adaptive n-step learning提升了训练的效率。
3. 结合deep neuroevolution和policy gradient

---

# 系统建模

1. 多UE(用户设备)，单个ES(边缘服务器)
2. 目标：最小化 $latency+energy$

<img src="/img/dis_model.png" width="500" />

---

# 算法

<div class="grid grid-cols-[570px,300px] gap-4">

<div>

## Actor Critic framework

![](/img/dis_actor.png)

</div>

<div>

# 特点

1. 长期来看，效果较直接学习q值更好

2. 训练时间较长
</div>

</div>

---

# 分布式训练

<div></div>

![](/img/dis_train.png)

---

# Adaptive N-Step Learning
G. Barth-Maron et al., “Distributed distributional deterministic policy gradients,” 2018

$$
\begin{aligned}
\mathcal{T} Q\left(S_{t}, A_{t} \mid \theta\right)=& R_{t}+\gamma R_{t+1}+\gamma^{2} R_{t+2}+\ldots+\gamma^{n-1} R_{t+n-1} \\
& \gamma^{n} \cdot \mathbb{E}\left[Q\left(S_{t+n}, \pi\left(S_{t+n} \mid \phi^{\prime}\right) \mid \theta^{\prime}\right)\right]
\end{aligned}
$$

# Deep Neuroevolution and Policy Gradient
H. Beyer, “Evolution strategies,” Scholarpedia, vol. 2, no. 8, 2007, Art. no. 1965.

1. 与遗传算法相结合，保证收敛。
2. 向输出中添加噪声。
3. 选择其中表现较好的模型。

---

# 实验

<div></div>

<div class="grid grid-cols-[400px,500px] gap-4">

<img src="/img/dis_eva.png" width="500" />

<img src="/img/dis_red.png" width="500" />

</div>
---
layout: two-cols
---

# 总结

1. 深度强化学习训练成本较高

2. 不同环境共同训练一个模型，使用这个模型进行初始化

3. 在训练中使用一些trick（剪裁梯度、启发式等）提高训练效率和泛化能力

# 计划

1. 实现网络层传输

2. 考虑使用分布式或者迭代的方法优化

---

<!-- <div class="grid grid-cols-2 gap-4">

<div>

</div>

<div>

</div>

</div> -->

---

---
class: 'text-center'
layout: cover
highlighter: shiki
download: true
info: |
  ## 近期工作汇报

  使用深度强化学习算法优化边缘计算任务卸载问题

  [范也]() at [Oct 11th 2021]()
---

# 近期工作汇报

#### 使用深度强化学习算法优化边缘计算任务卸载问题


范也 MG21320002


---
layout: center
---

# 工作概要
1. 调查20几篇DRL+任务卸载的论文
2. 完成基本的实验框架，包含
	1. 边缘计算任务卸载的模拟环境
	2. 使用较先进的DRL算法：T3C、SAC、PPO进行调度

---
layout: center
---

# 后续工作
1. 对现有的论文进行较详细的排查，找到比较好的优化目标
	1. 优化现有的环境和算法
	2. 调参
2. 整合discrete action的DRL算法
3. 实现baseline：贪心、穷举、无调度、线性松弛、DQN

---
layout: two-cols
---
<template v-slot:default>

## MEC offloading
1. 相对于云计算
2. 工厂
3. 任务调度：最优化问题
	1. 传统方式、遗传算法
	2. 强化学习算法

$$
\begin{array}{ll}
\min _{(\mathbf{a})} & 电量 + 速度, \\
\text { s.t. } & a_{i} \in\{0,1\}, \forall i \in \mathcal{M},
\end{array}
$$
</template>

<template v-slot:right>

![](/img/mec.png)

</template>

---

![](/img/frame.png)

---
layout: two-cols
---

# 读论文
DRL + MEC offloading + Lyapunov + ...
1. 使用的DRL算法比较落后：REINFORCE、DDPG、A3C、DQN
2. 算法框架基本一样，都是简单的模拟环境+DRL算法
3. 优化目标（公平性、效率、安全性、电量）、考虑的环境（多agent、连续、离散、时间分配方式）各有不同

先实现基本的框架，根据具体目标进行微调

::right::

![](/img/ddpg.png)

---

![](/img/net.png)

---
layout: two-cols
---


## 模拟实现

1063 line

考虑了

1. 电量
2. 处理速度
3. 任务缓冲
4. 数据传输
5. 信道


::right::


## DRL算法

大概1000 line

  已包含大部分连续动作空间算法：
  - TD3、PPO、SAC、DDPG

  拟实现其他离散空间算法：
  - D3QN、D4PG(连续)

---
layout: two-cols
---

## 排查
将现有论文中的
- 优化目标
- 考虑的要素 
- 理论阐述
- 环境配置

进行总结找出比较好的优化目标进行微调

::right::

## 实验

<br/>

- baseline：
  贪心、穷举、无调度、线性松弛、DQN
- discrete：
  D3QN、TD3

---
layout: center
---

# 总结

#### 基本实现实验框架，包含模拟环境和调度算法

后续工作：

1. 选择更新颖的优化目标和环境设置

2. 调参、基线实验

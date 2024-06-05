# Self_Opt_learn 学习计划
## 5月1日-5月20日
1、熟悉掌握single allocation p-hub median problem 、TSP、CVRP（capacitated VRP）、MDVRP（multi-depot VRP）、VRPTW（VRP with time window）五个基本组合优化问题的定义，能够写出数学模型，能够对着数学模型中的目标函数、约束条件解释其物理意义；

2、学习数学规划求解器gurobi的使用方法，能够使用gurobi对五个基本组合优化问题进行确定性求解，在小规模的测试数据上能够获得最优解；

3、能够针对性设计Genetic Algorithm对五个基本组合优化问题进行求解，在小规模测试数据上和最优解对比gap；在大规模测试数据上求解五个问题；测试数据见github仓库连接：https://github.com/oldsunsir/buaa_opt_learn

# GA算法学习参考
## 1、[交叉算子（动画演示）](https://blog.csdn.net/hba646333407/article/details/103349279)
单点交叉（Single-point crossover）<br>
两点交叉（Two-points crossover）<br>
多点交叉（Multi-point crossover）<br>
部分匹配交叉（Partially-matched crossover，PMX）<br>
均匀交叉（Uniform crossover）<br>
顺序交叉（Order Crossover，OX）<br>
基于位置的交叉（Position-based Crossover，PBX）<br>
基于顺序的交叉（Order-Based Crossover，OBX）<br>
循环交叉（Cycle Crossover，CX）<br>
子路径交叉交叉（Subtour Exchange Crossover，SEX）
## 2、[GA算法中各种选择策略解释与代码](https://www.cnblogs.com/zywnnblog/p/15988325.html)

# 实例
## 1、Single allocation p-hub median problem

单一分配P-Hub中位数问题（Single-Allocation P-Hub Median Problem）是一个组合优化问题，主要应用于运输和物流网络规划中。该问题涉及到确定一个最优的仓库（hub）位置，以便最小化货物运输的总成本或最大化网络的效率。

## 2、TSP（Traveling Salesman Problem）

旅行商问题，又称TSP问题。假设有一个旅行商人要拜访N个城市,他必须选择所要走的路径,路径的限制是每个城市只能拜访一次,而且最后要回到原来出发的城市。路径的选择目标是要求得的路径路程为所有路径之中的最小值。

<div align="center">
  <img src="https://quicklatex.com/cache3/3d/ql_f63bc0257e8c29c866d672dc2d17a43d_l3.png" alt="Description" width="500">
</div>

![Equation](https://latex.codecogs.com/svg.image?c_{ij}) 是各个城市点之间的距离。 ![Equation](https://latex.codecogs.com/svg.image?x_{ij}) 表示是否选择这个城市。最后一个不等式约束的含义解释如下：

<div align="center">
  <img src="https://github.com/Manpopp/Self_Opt_learn/blob/main/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20240519122526.png" alt="Example Image" width="600">
</div>

## 3、CVRP（capacitated VRP）

经典VRP可描述为：对一系列装卸货点进行适当的路径规划，在满足约束条件（客户需求、车辆载重和容积、车型、车辆行驶里程、配送时间窗、配送中心数量等限制）和目标最优化（路程最短、成本最低、使用车辆数最少、配送时间最快等）下，将客户的配送需求从配送中心送达客户点，或从客户点送回配送中心。

有能力约束的车辆路径调度（Capacitated Vehicle Routing Problem,CVRP）有能力约束的车辆路径问题,简称车辆路径问题。此模型是车辆路径问题的基本模型。该模型约束少,一般仅对车辆的载重和行驶的时间(或距离)有约束。此模型研究的时间最长,取得的成果最多,大量的精确算法,启发式算法用于求解此问题,其他模型的各种求解算法也大多衍生于此。

### 3.1 场景描述

单向：纯取货或纯送货；<br>
单配送中心：只有一个配送中心或车场；<br>
单车型：只考虑一种车型；<br>
需求不可拆分：客户需求只能有一辆车满足；<br>
车辆封闭：完成配送任务的车辆需回到配送中心；<br>
车辆充足：不限制车辆数量，即配送车辆需求均能满足；<br>
非满载：任意客户点的需求量小于车辆最大载重；

### 3.2 要求
优化目标：最小化车辆启动成本和车辆行驶成本之和；<br>
约束条件：车辆行驶距离约束，重量约束；<br>
已知信息：配送中心位置、客户点位置、客户点需求、车辆最大载重、车辆最大行驶距离、车辆启动成本、车辆单位距离行驶成本；<br>

### 3.3 数学模型

符号说明：
<div align="center">
  <img src="https://github.com/Manpopp/Self_Opt_learn/blob/main/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/20210427135610157.jpg" alt="Example Image" width="600">
</div>

数学模型：
<div align="center">
  <img src="https://github.com/Manpopp/Self_Opt_learn/blob/main/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/20210427135634136.jpg" alt="Example Image" width="600">
</div>



## 4、MDVRP（multi-depot VRP）

多车场车辆路径规划(Multi-Depot Vehicle Routing Problem，MDVRP)是指在一个区域内有多个中心场地和一定数量的客户点，需要派遣车辆从中心场地出发，分别到达客户点进行服务，最终回到相应的中心场地。该问题是一个NP困难问题，因此需要有效的求解算法。

### 4.1、参考资源

【1】邹彤,李宁,孙德宝,等. 多车场车辆路径问题的遗传算法[J]. 计算机工程与应用,2004,40(21):82-83. DOI:10.3321/j.issn:1002-8331.2004.21.025.
【2】Surekha P, Sumathi S. Solution to multi-depot vehicle routing problem using genetic algorithms[J]. World Applied Programming, 2011, 1(3): 118-131.
【3】[多车场路径优化丨遗传算法求解MDCVRP问题]( https://blog.csdn.net/weixin_53924466/article/details/132611846?ops_request_misc=&request_id=&biz_id=102&utm_term=MDVRP%20%20%E9%81%97%E4%BC%A0%E7%AE%97%E6%B3%95%20GA&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-132611846.142^v100^pc_search_result_base9&spm=1018.2226.3001.4187)
【4】Karakatič S, Podgorelec V. A survey of genetic algorithms for solving multi depot vehicle routing problem[J]. Applied Soft Computing, 2015, 27: 519-532.

## 5、VRPTW（VRP with time window）

有时间窗车辆路径问题（vehicle routing problems with time windows，VRPTW）车辆路线问题（VRP）最早是由Dantzig和Ramser于1959年首次提出，它是指一定数量的客户，各自有不同数量的货物需求，配送中心向客户提供货物，由一个车队负责分送货物，组织适当的行车路线，目标是使得客户的需求得到满足，并能在一定的约束下，达到诸如路程最短、成本最小、耗费时间最少等目的。

[遗传算法（GA）求解带时间窗的车辆路径（VRPTW）问题MATLAB代码](https://mp.weixin.qq.com/s?__biz=MzU2NDc1MTE3Mg==&mid=2247485520&idx=1&sn=294805dfcc471e2813a0da8388999594&chksm=fc47767bcb30ff6d013796a2382046d0d09778f61bd54b84802b6bb16f48c0b1c29e6117b6ab&scene=21#wechat_redirect)



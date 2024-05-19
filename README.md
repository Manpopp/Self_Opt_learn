# Self_Opt_learn 学习计划
## 5月1日-5月20日
1、熟悉掌握single allocation p-hub median problem 、TSP、CVRP（capacitated VRP）、MDVRP（multi-depot VRP）、VRPTW（VRP with time window）五个基本组合优化问题的定义，能够写出数学模型，能够对着数学模型中的目标函数、约束条件解释其物理意义；

2、学习数学规划求解器gurobi的使用方法，能够使用gurobi对五个基本组合优化问题进行确定性求解，在小规模的测试数据上能够获得最优解；

3、能够针对性设计Genetic Algorithm对五个基本组合优化问题进行求解，在小规模测试数据上和最优解对比gap；在大规模测试数据上求解五个问题；测试数据见github仓库连接：https://github.com/oldsunsir/buaa_opt_learn

# GA算法学习参考
## 1、[交叉算子（动画演示）](https://blog.csdn.net/hba646333407/article/details/103349279)
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

有能力约束的车辆路径调度（Capacitated Vehicle Routing Problem,CVRP）有能力约束的车辆路径问题,简称车辆路径问题。此模型是车辆路径问题的基本模型。该模型约束少,一般仅对车辆的载重和行驶的时间(或距离)有约束。此模型研究的时间最长,取得的成果最多,大量的精确算法,启发式算法用于求解此问题,其他模型的各种求解算法也大多衍生于此。

## 4、MDVRP（multi-depot VRP）

多中心车辆路径规划(Multi-Depot Vehicle Routing Problem，MDVRP)是指在一个区域内有多个中心场地和一定数量的客户点，需要派遣车辆从中心场地出发，分别到达客户点进行服务，最终回到相应的中心场地。该问题是一个NP困难问题，因此需要有效的求解算法。

## 5、VRPTW（VRP with time window）

有时间窗车辆路径问题（vehicle routing problems with time windows，VRPTW）车辆路线问题（VRP）最早是由Dantzig和Ramser于1959年首次提出，它是指一定数量的客户，各自有不同数量的货物需求，配送中心向客户提供货物，由一个车队负责分送货物，组织适当的行车路线，目标是使得客户的需求得到满足，并能在一定的约束下，达到诸如路程最短、成本最小、耗费时间最少等目的。

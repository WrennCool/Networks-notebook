# algorithm for basic network quantities
# 基础网络指标的算法

计算度数、聚类系数、最短路径、介数、最大流（maximum flow）等算法

## <font color = deepskyblue> Degree </font>
## <font color = deepskyblue> 度 </font>

如果网络是采用邻接表方式存储在计算机中，那么计算一个节点的度数只需要找到其在邻接表中对应的序号就可以了，该方法计算复杂度为O（1）

如果网络以邻接矩阵的方式表示，计算某节点的度值需要遍历某行所有的元素，其计算复杂度为O（n）

## <font color = deepskyblue> Clustering coefficients </font>
## <font color = deepskyblue> 聚类系数 </font>

### 局部聚类系数
该指标表示节点的所有邻居中具有连边的邻居节点比例

$$C_{i}=\frac{\text { (number of pairs of neighbors of } i \text { that are connected) }}{\text { (number of pairs of neighbors of } i)}$$
计算该指标时应考虑节点i所有可能成对的节点u,v，判断可能的节点对是否有边连接，总判断次数为$\frac{k_i}{2(k_i-1)}$,


### 全局聚类系数
$$C_{i}=\frac{\text { number of triangles} \times 3}{\text { number of connected triples}}$$

所有可能的三元组中成型的三角形的比例，对于网络中的每个节点，我们都考虑其邻居节点是否有连接，是否能组成三角形，我们将所有节点此类边的总数相加并除以三角形数，总判断次数为$\sum_i\frac{k_i}{2(k_i-1)}$


$$\begin{array}{c}
\sum_{i} \frac{1}{2} k_{i}\left(k_{i}-1\right)=\frac{1}{2} n\left(\left\langle k^{2}\right\rangle-\langle k\rangle\right) \\
\langle k\rangle=\frac{1}{n} \sum_{i} k_{i} \\
\quad\left\langle k^{2}\right\rangle=\frac{1}{n} \sum_{i} k_{i}^{2}
\end{array}$$

对于无标度网络，其度均值表现无异样，但度均方却提示网络度分布较为发散，实际上契合无标度网络的度 幂律分布特点，如此采用二阶矩方式计算网络的聚类系数将难免会使计算复杂度大幅提高，因此采用替代算法如。。。是非常有必要的
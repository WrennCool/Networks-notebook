# Similarity 相似性
在网络中，为了匹配与给定节点最为相似的节点
- **structural equivalence 结构相似性:**
两个节点共享相同的邻居节点，如一个家庭内部两兄弟或姐妹，在亲属关系网络中该二节点都拥有同样的邻居（亲属）

- **Regular equivalence 规则相似性:**
两个节点的邻居是相似的，如某公司两个子公司的中层领导，在上下属关系网络中，该二节点的上司节点是具有结构相似性的，即拥有同样的总公司领导

![结构相似性与规则相似性](C7-pic/c7-6.png)

## Structural equivalence 结构相似性
1. 直接衡量两点共同邻居的数量，即 $n_{ij} = \sum_k A_{ik} A_{ij}$。
    - 节点间的相似性是一个相对概念，所以具体的邻居数无法作为两节点‘谁更与某节点相似’的节点，我们需要采用归一化的方法来校正这一误差，因此下式提供校正i、j节点自身度数的方法
2. 采用**余弦相似性**方法(cosine similarity)(Salton’s cosine)来衡量两节点相似性
    - > 余弦相似性通过测量两个向量的夹角的余弦值来度量它们之间的相似性，0度角的余弦值是1，而其他任何角度的余弦值都不大于1；并且其最小值是-1。从而两个向量之间的角度的余弦值确定两个向量是否大致指向相同的方向
    - > <img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/2a8c50526e2cc7aa837477be87eff1ea703f9dec" width="400px">
    - 我们将一个网络的邻接矩阵的i行与j行视为两个向量，采用计算两向量余弦相似性的方法计算其结构相似性得：

    - $\sigma_{i j}=\cos \theta=\frac{\sum_{k} A_{i k} A_{k j}}{\sqrt{\sum_{k} A_{i k}^{2}} \sqrt{\sum_{k} A_{j k}^{2}}} = \frac{n_ij}{\sqrt{k_i k_j}}$

    - 最后一个等式只适用于无权网络，对于度值为0的节点，其相似度 $n_ij = 0$


    - 以下将是一个案例展示（等我会画图了再来补）
3. 另外一个将相似性规约到0-1之间的相似度为**Jaccard coefficient**
   - $J_{i j}=\frac{n_{i j}}{k_{i}+k_{j}-n_{i j}}$

4. 采用**皮尔逊相关系数**（Pearson correlation coefficient）衡量两节点邻居的相似性
   -  $r_{i j}=\frac{\sum_{k}\left(A_{i k}-\left\langle A_{i}\right\rangle\right)\left(A_{j k}-\left\langle A_{j}\right\rangle\right)}{\sqrt{\sum_{k}\left(A_{i k}-\left\langle A_{i}\right\rangle\right)^{2}} \sqrt{\sum_{k}\left(A_{j k}-\left\langle A_{j}\right\rangle\right)^{2}}}$

5. 度量两节点向量的误差来衡量两节点的相似性
   - $h_{i j}=\sum_{k}\left(A_{i k}-A_{j k}\right)^{2}$]\
 ##  Regular equivalence规则相似性
 
 

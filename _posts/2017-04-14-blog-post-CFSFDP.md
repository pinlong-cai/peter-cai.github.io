---
title: 'CFSFDP聚类算法'
date: 2015-08-14
permalink: /posts/2017-04-14-blog-post-CFSFDP/
tags:
  - 知识积累
  - 数据挖掘
  - 算法
mathjax: true
---

!['Clustering'](images/CFSFDP-Clustering.jpg)

>聚类分析又称聚类，是把一个数据集合划分为多个集群（cluster）的过程，使得相同集群内的数据之间具有相似性，不同集群的数据之间具有差异性。聚类是数据挖掘、统计分析的主要任务之一，应用于机器学习、模式识别、图像处理、信息检索、生物信息、数据压缩和计算机图像等领域。（From 维基百科）

# 1  聚类算法总结

&emsp;&emsp;常用的聚类算法包括：

* （1）启发式分割算法：起始确定K个中心点，用距离公式来判断数据点归属，用代价函数（如最小化平方和）评价聚类结果，迭代直至最优，例如：K-Means，K-Medoids。
* （2）基于模型的算法：起始随机确定若干个模型中心，用基于概率的方法判断数据点归属，通过迭代的方法找寻适合各个类的模型，例如：Gaussian Mixture Model。
* （3）降维的方法：通过降维，找寻数据间的特征，再完成聚类，例如：Spectral Clustering，Normalised-Cut。
* （4）基于密度的方法：定义数据点密度，从少数对象开始拓展得到集群，例如：DBSCAN，CFSFDP。
<!-- more -->
&emsp;&emsp;根据聚类的数据特征应合理选用聚类算法。如图1所示，包含球形集群和非球形集群两幅典型示意图，在球形集群中，数据集相对集中，且无空间分布规律特征，这时候常常采用K-means、K-medoids、Gaussian Mixture Model等方法来聚类。而对于非球形集群，数据点分布具有空间特征，图1（b）所示的是具有三个集群的数据集，三个集群的数据点分布呈现类渐开线特征，这时就不能采用传统的聚类方法，而应选择Spectral Clustering、Normalised-Cut、DBSCAN和CFSFDP等等。

!['图1'](\images\CFSFDP-图1.jpg)图1

# 2  CFSFDP聚类算法

&emsp;&emsp;CFSFDP算法即为Clustering by fast search and find of density peaks，这是由Alex Rodriguez 和Alessandro Laio于2014年发表在《Science》期刊的聚类算法。该算法的基本假设有两个，一是聚类中心附近的数据点具有较低的密度，而是数据点与其他密度更大的中心距离较远。数据点密度的定义为：

$$\rho_i=\sum_j\chi(d_{ij}-d_c)$$

这里，当$x>0$时，$\chi(x)=1$，当$x<0$时，$\chi(x)=0$。其中，$d_c$为截断距离（Cutoff distance），即确定密度的重要阈值，文中提到$d_c$取合适值使得平均密度为总数据量的1%-2%。数据点与密度较大点间的最小距离定义为：

$$\delta_i=\left\{
\begin{aligned}
\min_{j:\rho_j>\rho_i}(d_{ij}),\quad if\quad \rho_i<\max\{\rho_i\} \\
\max_j(d_{ij}),\quad if\quad\rho_i=\max\{\rho_i\}
\end{aligned}
\right.
$$

&emsp;&emsp;在文中的例子中，数据集如图2（a）所示，分别计算出$\delta$和$\rho$，在所有的数据点中，有四种点，一是$\delta$大$\rho$大的点，包括1和10；二是$\delta$大$\rho$小的点，包括28，26，27；三是$\delta$小$\rho$大，包括7，8，3，4等等，四是$\delta$小$\rho$小，其余点都是这个类别。很明显，第一种点即为集群的中心，第二类则是离群点。文章中提到定义一个指标来选择中心，用$\delta$和$\rho$乘积的形式：

!['图2'](\images\CFSFDP-图2.jpg)图2

&emsp;&emsp;在确定数个中心之后，其余数据点按照密度大小，依次从属于距离最近的密度大于其自身的点。
&emsp;&emsp;根据该聚类算法的步骤，我自己设计了类渐开线数据集的聚类实验，聚类结果如图3所示。图3（a）是K-means的聚类结果，很明显这种方法未能实现非球形聚集的聚类问题，而CFSFDP算法则能够实现目标。然而，在实验中发现参数$d_c$的选择很大程度上影响了实验结果，很难确定。 

!['图3'](\images\CFSFDP-图3.jpg)图3

# 3  阈值讨论——Data Field

&emsp;&emsp;由于参数$d_c$是CFSFDP算法中重要的影响因素，因此其确定方法引起了一些学者的兴趣，其中有Wang等人提出了使用名为Data Filed的方法来确定。他们定义每个数据点的潜力（Pontential）为：

$$\phi_i=\sum_{j=1}^n m_jK(\frac{x_i-x_j}\sigma)$$

这里，而所以数据点潜力可组成的数据场（Data Filed），其范围由最小化的熵值H（Entropy）来确定，公式为：

$$H=-\sum_{i=1}^n\frac{\phi_i}{Z}\ln{\frac{\phi_i}{Z}}$$

&emsp;&emsp;求出数据点的潜力公式中的$\sigma$从而确定空间中的数据场。他们比较了数据场的热力图和CFSFDP算法得到的聚类结果图，发现二者很相近，因此就认为$d_c$的确定可以由数据场的方法来实现。当潜力公示的核函数用高斯函数的时候，高斯函数具有“3$\sigma$准则”，因此$d_c$的取为$\frac{3}{\sqrt{2}}\sigma$，表示数据点的影响范围。这里的取值较为难理解，一般都是直接用均值$\pm3\sigma$的区间。然而，从他们的实验对比中，可以发现这种确定方法得到较好的聚类结果，相关成果发表的论文得到了84次的引用量。

# 4  改进策略1——借助Chameleon模型

&emsp;&emsp;Zhang等人提出CFSFDP算法不适用与一些特殊的数据集，例如图4所示的数据集合。这个数据集其实是由三个数据集群组成的，外围集群、内左集群和内右集群，但是Zhang等人用CFSFDP算法来聚类，尝试用不同的$d_c$值，都难以得到好的聚类结果，如图5所示。因此，他们研究了改进的策略。

!['图4'](\images\CFSFDP-图4.jpg)图4

!['图5'](\images\CFSFDP-图5.jpg)图5

&emsp;&emsp;Zhang等人的改进策略是受Chameleon模型启发，该模型的基本思想如图6所示，包括三个步骤，一是将数据集合用k近邻图的方法，组成稀疏图，而是将稀疏图打散分成若干个小类，三是重新组合，得到最后的聚类结果。
<div align=center>
<img src="..\images\CFSFDP-图6.jpg" /> 图6
<p>图6</p>  
</div>
&emsp;&emsp;Chameleon算法定义了两个概念，相对互关联（Relative inner-connectivity）代表小类之间的连接区域强度的总和，相对紧密度（Relative closeness）则代表小类之间的连接区域强度的平均值。两个指标都有相应的公式，并进行标准化，然后结合两个指标来合并小类。
借助这种思想，Zhang等人设置较小的$d_c$，然后用CFSFDP聚成数目较多的小类，之后再合并成集群，图7所示即为他们文中的实验。先讲两个U型集群组成的数据划分为若干个小类，再用Chameleon算法来合并小类，最终得到结果。

# 5  改进策略2——一些改进措施

&emsp;&emsp;Gao等人在文章中总结了CFSFDP算法在实际应用中遇到的问题：

!['图7'](\images\CFSFDP-图7.jpg)图7

* （1）截断距离dc需要依靠先验经验确定；
* （2）集群中心选择需要主观地从决策图中选择；
* （3）相同的高密度峰会算法会失效；
* （4）算法无法应用与特殊的数据集。

&emsp;&emsp;Gao等人在文中提出了改进的模型ICFS，模型的具体步骤如图8所示，分成：预聚类、合并、拆分三个阶段。

!['图8'](\images\CFSFDP-图8.jpg)图8

&emsp;&emsp;预聚类阶段，他们重新定义了$d_c$的确定公式、中心的选择方式和分配策略。其中，中心的选择方式是在原有算法利用$\delta$和$\rho$乘积的形式，将得到$\gamma$值从大到小排列，然后分别再乘以密度$\rho$，将新的决策图（decision graph）与原有的决策图对比，从新的$\gamma^\prime$值开始，第一次出现阶跃点（Bump point）的时候，即有$\gamma_k^\prime>\gamma_{k+1}^\prime\&\gamma_k^\prime>\gamma_{k-1}^\prime$，则将1到k所以数据点作为中心，这个过程如图9所示。

!['图9'](\images\CFSFDP-图9.jpg)图9

&emsp;&emsp;分配策略改变原有的“从属最近的较高密度点”分配，而是“使非中心点优先从属于最近的相同密度点”，如图10所示。然而这种分配方式也不完全合理，在对于相同密度的A和B，先分配A或者先分配B得到的结果是不同的。

!['图10'](\images\CFSFDP-图10.jpg)图10

&emsp;&emsp;完成预聚类之后，Gao等人也提出了类合并和拆分的策略，合并是根据最近邻图的方法，而拆分则是根据“同一类中不能同时含有两个阶跃点”的准则。

# 6  总结
&emsp;&emsp;聚类算法在数据挖掘中是常用且重要的算法，但应用数据集特征不同，可能要先挑选合适的算法。CFSFDP算法是新颖的基于密度的聚类算法，给我们提供了一种新的聚类思路，方式具有普适性，得到不少学者的认可。然而，算法的本身的参数阈值确定和逻辑规则还有待改进。当然，改进算法也不是越复杂越好，太过于复杂的算法可能就会失去普适性，因此，改进策略需要在后续研究中进一步尝试。

# 参考文献
* [1] Alex Rodriguez and Alessandro Laio. Clustering by fast search and find of density peaks. Science 344, 1492 (2014).
* [2] Wang S, Wang D, Li C, et al. Comment on "Clustering by fast search and find of density peaks". Computer Science, 2015.
* [3] Wang S, Wang D, Li C, et al. Clustering by fast search and find of density peaks with data field. Chinese Journal of Electronics, 2016, 25(3):1492-6.
* [4] Zhang W, Li J. Extended fast search clustering algorithm: widely density clusters, no density peaks. Computer Science, 2015.
* [5] Karypis G, Han E H, Kumar V. Chameleon: hierarchical clustering using dynamic modeling. Computer, 1999, 32(8):68-75.
* [6] Gao J, Zhao L, Chen Z, et al. ICFS: An improved fast search and find of density peaks clustering. 2016 IEEE 14th Intl Conf on Dependable, Autonomic and Secure Computing, 14th Intl Conf on Pervasive Intelligence and Computing, 2nd Intl Conf on Big Data Intelligence and Computing and Cyber Science and Technology Congress. 2016:537-543.

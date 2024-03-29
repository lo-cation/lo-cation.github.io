---
layout: post
title: 线性规划的基本性质
date:   2020-08-06
tags: 学习
---
线性规划是数学规划的一个重要分支，在实践上有着广泛的应用，比如微观经济学和商业管理领域中减低生产过程成本等。  
## 标准形式
$$
\begin{align}
min \quad \sum\limits_{j=1}^{n}c_{j}x_{j} &\\
s.t \quad \sum\limits_{j=1}^{n}a_{ij}x_{j} &= b_{i} \qquad i = 1,...,m\\
x_{j} &\geq 0 \qquad j=1,...,n\\
\end{align}
$$  
标准形式也可以写成矩阵形式：  
$$
\begin{align}
min \quad cx\\
s.t \quad Ax &= b\\
x &\geq 0
\end{align}
$$  
其中$A$是$m \times n$矩阵，$c$是$n$维行向量，$b$是$m$维列向量。  
若给定的数学模型不是标准形式的，可以通过引入松弛标量，将非标准形式化为标准形式。
如给定问题为：  
$$
\begin{align}
min \quad \sum\limits_{j=1}^{n}c_{j}x_{j} &\\
s.t \quad \sum\limits_{j=1}^{n}a_{ij}x_{j} &\leq b_{i} \qquad i = 1,...,m\\
x_{j} &\geq 0 \qquad j=1,...,n
\end{align}
$$  
可化为下列标准形式：  
$$
\begin{align}
min \quad \sum\limits_{j=1}^{n}c_{j}x_{j} & \qquad j=1,...,n\\
s.t \quad \sum\limits_{j=1}^{n}a_{ij}x_{j} + x_{j+i} &= b_{i} \qquad i = 1,...,m\\
x_{j} &\geq 0 \qquad j=1,...,m+n\\
\end{align}
$$

## 基本性质

* 可行域  
线性规划的可行域是凸集。

* 最优极点  
若给定的线性优化问题存在有限最优解，则目标函数的最优解可在某个极点上达到。

* 最优基本可行解  
设矩阵$A$的秩为$m$，可以对$A$进行列变换与分块，使$A = [B,N]$， 其中$B$是$m$阶可逆矩阵。
同样可以将$x$记作$x = [x_B, x_N]^T$，其中$x_B$和$x_N$是与$B$和$N$对应的分量。
则$Ax=b$可以写作$Bx_B+Nx_N=b$。
由于$x_N$是自由未知量，可令$x_N=0$，可解得$x_B = B^{-1}b$。
称$B$为基（矩阵），$x_B$为一组基，其变量为基变量，$x_N$为非基变量。若$B^{-1}b \geq 0$，则称$x$为约束条件$Ax=b, \quad x\geq 0$的基本可行解，$B$为可行基矩阵。

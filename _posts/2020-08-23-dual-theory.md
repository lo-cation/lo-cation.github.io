---
layout: post
title: 对偶理论
date:   2020-08-23
tags: 学习
---
线性规划中普遍存在配对现象，即对每一个线性规划问题，都存在另一个与它密切相关的线性规划问题。在配对的像个问题中，一个称为原问题，另一个成为它的对偶问题。对偶理论即是研究揭示每对问题内在联系的理论。  
## 对偶问题的表达
### 对称形式
原问题：  
$$\begin{align*} \tag{1}
  min \quad c_{1 \times n}x_{n \times 1} &\\
  s.t \quad A_{m \times n}x_{n \times 1} &\geq b_{m \times 1}\\
  x_{n \times 1} &\geq 0 
\end{align*}$$

对偶问题：  
$$\begin{align*} \tag{2}
  max \quad \omega_{1 \times m}b_{m \times 1} &\\
  s.t \quad \omega_{1 \times m}A_{m \times n} &\leq c_{1 \times n}\\
  \omega_{1 \times m} &\geq 0 
\end{align*}$$

原问题的约束条件个数等于对偶变量的个数，而原问题中变量的个数等于对偶问题中约束条件的个数。

### 非对称形式
考虑具有等式约束的线性规划问题，原问题为：  
$$\begin{align*} \tag{3}
  min \quad c_{1 \times n}x_{n \times 1} &\\
  s.t \quad A_{m \times n}x_{n \times 1} &= b_{m \times 1}\\
  x_{n \times 1} &\geq 0 
\end{align*}$$  
可以将等式约束变为一组“$\geq$”和“$\leq$”约束:  
$$\begin{align*}
  min \quad c_{1 \times n}x_{n \times 1} &\\
  s.t \quad A_{m \times n}x_{n \times 1} &\geq b_{m \times 1}\\
      \quad -A_{m \times n}x_{n \times 1} &\geq -b_{m \times 1}\\
  x_{n \times 1} &\geq 0 
\end{align*}$$  
那么对偶问题为：  
$$\begin{align*}
  max \quad u_{1 \times m}b_{m \times 1} - v_{1 \times m}b_{m \times 1}&\\
  s.t \quad u_{1 \times m}A_{m \times n} - vA_{m \times n}&\leq c_{1 \times n}\\
  u_{1 \times m}, v_{1 \times m} &\geq 0 
\end{align*}$$  
令$\omega = u-v$则$\omega$不再具有非负限制，于是可以得到：  
$$\begin{align*} \tag{4}
  max \quad \omega_{1 \times m}b_{m \times 1} &\\
  s.t \quad \omega_{1 \times m}A_{m \times n} &\leq c_{1 \times n}
\end{align*}$$

### 一般形式
一般形式考虑问题中同时含有“$\geq$”，“$\leq$”及“=”几种约束，需要采取引入松弛变量的方法来找到对偶形式。设原问题为：  
$$\begin{align*}
  min \quad c_{1 \times n}x_{n \times 1} &\\
  s.t \quad A^1_{m_{1} \times n}x_{n \times 1} &\geq b^1_{m_{1} \times 1}\\
      \quad A^2_{m_{2} \times n}x_{n \times 1} &= b^2_{m_{2} \times 1}\\
      \quad A^3_{m_{3} \times n}x_{n \times 1} &\leq b^3_{m_{3} \times 1}\\
      x_{n \times 1} &\geq 0 
\end{align*}$$  
引入松弛变量并写为矩阵形式后：  
$$\begin{align*}
  min \quad c_{1 \times n}x_{n \times 1} + 0 \cdot x^s_{n_1 \times 1} + 0 \cdot x^t_{n_3 \times 1} &\\
  s.t \quad \begin{bmatrix} A^1_{m_{1} \times n} & -I_{m_{1} \times n_1} & 0\\
                   A^2_{m_{2} \times n} & 0 & 0 \\
                   A^3_{m_{3} \times n} & 0 & I_{m_{3} \times n_3}\\
            \end{bmatrix}
            \begin{bmatrix} x_{n \times 1}\\
                            x^s_{n_1 \times 1}\\
                            x^t_{n_3 \times 1}
            \end{bmatrix}
            &=
            \begin{bmatrix} b^1_{m_{1} \times 1}\\
                            b^2_{m_{2} \times 1}\\
                            b^3_{m_{3} \times 1}
            \end{bmatrix}\\
      x_{n \times 1}, x^s_{n_1 \times 1}, x^t_{n_3 \times 1} &\geq 0 
\end{align*}$$  
利用非对称对偶的处理方法，可以得到以上问题对偶问题：  
$$\begin{align*}
  max \quad \omega^1_{1 \times m_{1}}b^1_{m_{1} \times 1} + \omega^2_{1 \times m_{2}}b^2_{m_{2} \times 1} + \omega^3_{1 \times m_{3}}b^3_{m_{3} \times 1} &\\
  s.t \quad \begin{bmatrix} \omega^1_{1 \times m_{1}} & \omega^2_{1 \times m_{2}} & \omega^3_{1 \times m_{3}} \end{bmatrix}
	    \begin{bmatrix} A^1_{m_{1} \times n} & -I_{m_{1} \times n_1} & 0\\
                   A^2_{m_{2} \times n} & 0 & 0 \\
                   A^3_{m_{3} \times n} & 0 & I_{m_{3} \times n_3}\\
            \end{bmatrix}
            & \leq
            \begin{bmatrix} c_{1 \times n} & 0 & 0 \end{bmatrix}\\
\end{align*}$$  
即：  
$$\begin{align*}
  max \quad \omega^1_{1 \times m_{1}}b^1_{m_{1} \times 1} + \omega^2_{1 \times m_{2}}b^2_{m_{2} \times 1} + \omega^3_{1 \times m_{3}}b^3_{m_{3} \times 1} &\\
  s.t \quad \omega^1_{1 \times m_{1}} A^1_{m_{1} \times n} + \omega^2_{1 \times m_{2}}A^2_{m_{2} \times n} + \omega^3_{1 \times m_{3}}A^3_{m_{3} \times n} \leq c_{1 \times n}\\
      \quad \omega^1_{1 \times m_{1}} &\geq 0\\
      \quad \omega^3_{1 \times m_{3}} &\leq 0
\end{align*}$$  

## 对偶定理
由于不同形式的对偶可以相互转化，因此下面仅关于对称对偶问题，即以上（1）和（2），叙述几个重要定理及推论，这些结论对其他形式的对偶仍然成立。  
### 定理1
设$x^{(0)}$和$\omega^{(0)}$分别是（1）和（2）的可行解，则$cx^{(0)}\geq\omega^{(0)}b$。  
#### 推论1
若$x^{(0)}$和$\omega^{(0)}$分别是（1）和（2）的可行解，且$cx^{(0)}=\omega^{(0)}b$，则$x^{(0)}$和$\omega^{(0)}$分别是（1）和（2）的最优解。  
#### 推论2
对偶规划（1）和（2）有最优解的充要条件是它们同时有可行解。  

### 定理2
设（1）和（2）其中一个问题存在最优解，则另一个问题也存在最优解，且两个问题的目标函数的最优值相等。  
#### 推论1
若线性规划（1）存在一个对应基$B$的最优基本可行解，则单纯形乘子$\omega = c_{B}B^{-1}$是对偶问题（2）的一个最优解。  


## 互补松弛性质
在对偶问题中，当知道一个问题的最优解时，可以利用互补松弛定理求出另一个为问题的最优解。  
### 定理1
设$x^{(0)}$和$\omega^{(0)}$分别是（1）和（2）的可行解，那么$x^{(0)}$和$\omega^{(0)}$都是最优解的充要条件是，对所有$i$和$j$，下列关系成立：
1. 如果$x^{(0)}_j>0$，就有$\omega^{(0)}p_j=c_j$
2. 如果$\omega^{(0)}p_j<c_j$，就有$x^{(0)}_j=0$
3. 如果$\omega_i^{(0)}>0$，就有$A_i x^{(0)}=b_i$
4. 如果$A_i x^{(0)}>b_i$，就有$\omega_i^{(0)}=0$

其中$p_j$是$A$的第$j$列，$A_i$是$A$的第$i$行。


### 定理2
对于含等式约束的非对称形式的对偶规划，设$x^{(0)}$和$\omega^{(0)}$分别是（3）和（4）的可行解，那么$x^{(0)}$和$\omega^{(0)}$都是最优解的充要条件是，对所有$i$下列关系成立：
1. 如果$x^{(0)}_j>0$，就有$\omega^{(0)}p_j=c_j$
2. 如果$\omega^{(0)}p_j<c_j$，就有$x^{(0)}_j=0$

其中$p_j$是$A$的第$j$列。

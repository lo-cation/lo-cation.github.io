---
layout: post
title: 斜角直线坐标系的基矢量与矢量分量
date: 2022-05-24 22:30:00 +0800
tags: 学习    
---

## 平面内的斜角直线坐标系
### 协变基矢量
本部分考虑平面问题。平面中可以选出任意一组不共线的矢量 $\bf{g}_\alpha (\alpha=1,2)$ 作为参考矢量，则任意矢量 $\bf{P}$ 可以表示为：
$$
\bf{P} = P^\alpha\bf{g}_\alpha
$$
称参考矢量 $\bm{g}_\alpha$ 为**协变基矢量(covariant basis)**。

### 逆变基矢量
在同一平面内，存在唯一一组参考矢量 $\bm{g}^\beta (\beta=1,2)$ 满足对偶关系：
$$
\bm{g}^\beta \cdot \bm{g}_\alpha = \delta_{\alpha}^{\beta}
$$
式中 $\delta_{\alpha}^{\beta}$ 为Kronecker $\delta_{\alpha}^{\beta}$。当 $\alpha=\beta$ 时， $\delta_{\alpha}^{\beta}=1$，否则 $\delta_{\alpha}^{\beta}=0$。
并称参考矢量 $\bm{g}^\beta$ 为**逆变基矢量(contravariant basis)**。

记 $\varphi = <\bm{g}_1,\bm{g}_2>$，则
$$
|\bm{g}^1|=\frac{1}{|\bm{g}_1|sin(\varphi)}, \quad |\bm{g}^2|=\frac{1}{|\bm{g}_2|sin(\varphi)}
$$

### 矢量的分量
任意矢量 $\bm{P}$ 对协变基矢量 $\bm{g}_\alpha$ 分解的分量 $P^\alpha$ 称为矢量 $\bm{P}$ 的**逆变分量**：
$$
\bm{P} \cdot \bm{g}^\beta = P^\alpha\bm{g}_\alpha \cdot \bm{g}^\beta = P^\alpha \delta_{\alpha}^{\beta} = P^\beta
$$

任意矢量 $\bm{P}$ 对逆变基矢量 $\bm{g}^\beta$ 分解的分量 $P_\beta$ 称为矢量 $\bm{P}$ 的**协变分量**：
$$
\bm{P} \cdot \bm{g}_\alpha = P_\beta\bm{g}^\beta \cdot \bm{g}_\alpha = P_\beta \delta_{\alpha}^{\beta} = P_\alpha
$$

可以观察出，各个量的标记规律为：**下标为协变（矢量/分量），上边为逆变（矢量/分量）**。

## 三维空间中的斜角直线坐标系
### 协变基矢量
本部分考虑三维空间问题。在空间中可以选出任意一组线性无关的矢量 $\bm{g}_i (i=1,2,3)$ 作为参考矢量，则空间中任意一点的位置可以用坐标原点到该点的矢径 $\bm{r}$ 表示：
$$
\bm{r} = x^i \bm{g}_i = x^1 \bm{g}_1 + x^2 \bm{g}_2 + x^3 \bm{g}_3
$$
由上式可得矢径对坐标 $x^i$ 的微分：
$$
d\bm{r} = \frac{\partial \bm{r}}{\partial x^i} dx^i = \bm{g}_i dx^i
$$
并将矢径对坐标的偏导数 $\bm{g}_i$ 定义为**协变基矢量**，成为**自然基矢量**，即
$$
\bm{g}_i = \frac{\partial \bm{r}}{\partial x^i}
$$

### 逆变基矢量
与平面问题类似，由对偶关系可以得到唯一一组与协变基矢量 $\bm{g}_i$ 对应的逆变基矢量 $\bm{g}^j (j=1,2,3)$：
$$
\bm{g}^j \cdot \bm{g}_i = \delta_i^j
$$

### 由协变基矢量求逆变基矢量
#### 方法一
因 $\bm{g}^1$ 垂直于 $\bm{g}_2$ 与 $\bm{g}_3$ ，可令 $\bm{g}^1=a\bm{g}_2 \times \bm{g}_3$。又因 $\bm{g}^1 \cdot \bm{g}_1 = 1$ 可得：
$$
1 = \bm{g}^1 \cdot \bm{g}_1 = a(\bm{g}_2 \times \bm{g}_3) \cdot \bm{g}_1
$$
对固定的协变基矢量 $\bm{g}_i$，混合积 $(\bm{g}_2 \times \bm{g}_3) \cdot \bm{g}_1$ 为固定常数，可以由上式求的 $a$。
同理可求 $\bm{g}^2$ 与 $\bm{g}^3$。

#### 方法二
将逆变基矢量 $\bm{g}^i$ 对协变基 $\bm{g}_j$ 进行分解，即：
$$
\bm{g}^i = g^{ij} \bm{g}_j
$$
由对偶关系可知
$$
\bm{g}^i \cdot \bm{g}^j = g^{ik} \bm{g}_k \cdot \bm{g}^j = g^{ik} \delta_k^j = g^{ij}
$$
同理，协变基矢量 $\bm{g}_i$ 可以对逆变基矢量 $\bm{g}^j$ 分解：
$$
\bm{g}_i = g_{ij} \bm{g}^j
$$
且有
$$
\bm{g}_i \cdot \bm{g}_j = g_{ij}
$$
称 $g_{ij}$ 为**度量张量的协变分量**， $g^{ij}$ 为**度量张量的逆变分量**。

下面对 $g_{ij}$ 与 $g^{ij}$ 进行一些讨论。
* 由矢量内积的交换律可知 $g_{ij} = g_{ji}$，$g^{ij} = g^{ji}$，即由 $g_{ij}$ 与 $g^{ij}$ 各自构成的矩阵 $[g_{ij}]$ 与 $[g^{ij}]$ 为对称矩阵：
$$
[g_{ij}] = [g_{ij}]^T, \quad [g^{ij}] = [g^{ij}]^T
$$
其中，矩阵元素的前指标表示行号，后指标表示列号。

* 由对偶关系可知：
$$
\delta_i^j = \bm{g}_i \cdot \bm{g}^j = g_{ik} \bm{g}^k \cdot \bm{g}^j = g_{ik} g^{kj}
$$
即由 $g_{ij}$ 与 $g^{ij}$ 各自构成的矩阵互逆:
$$
[g^{ij}] = [g_{ij}]^{-1}
$$

* 若协变基矢量 $\bm{g}_i$ 构成右手系，逆变基矢量 $\bm{g}^j$ 也构成右手系。

### 指标升降关系
与平面问题类似，任意矢量 $\bm{P}$ 既可以对协变基矢量分解，有可以对逆变基矢量分解
$$
\bm{P} = P^i \bm{g}_i = P_j \bm{g}^j
$$
且有
$$
P^i = \bm{P} \cdot \bm{g}^i = P_k \bm{g}^k \cdot \bm{g}^i = P_k g^{ki} \\
P_j = \bm{P} \cdot \bm{g}_j = P^k \bm{g}_k \cdot \bm{g}_j = P^k g_{kj}
$$
上述两式称为矢量分量的**指标升降关系**。

基矢量也有类似的指标升降关系:
$$
\bm{g}^i = g^{ij} \bm{g}_j \\
\bm{g}_i = g_{ij} \bm{g}^j
$$
可以发现，起升指标作用的是度量张量的逆变分量 $g^{ij}$，起降指标作用的是度量张量的协变分量 $g_{ij}$。度量张量的分量可以把需要升降的矢量/矢量分量的指标转变为相同位置的指标，即变换后的指标位置与度量张量的分量指标位置相同。

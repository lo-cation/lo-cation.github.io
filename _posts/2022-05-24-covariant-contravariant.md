---
layout: post
title: 斜角直线坐标系的基矢量与矢量分量
date: 2022-05-24 22:30:00 +0800
tags: 学习    
---

## 平面内的斜角直线坐标系
### 协变基矢量
本部分考虑平面问题。平面中可以选出任意一组不共线的矢量 $$\bf{g}_\alpha$$ 作为参考矢量，则任意矢量 $$\bf{P}$$ 可以表示为：

$$
\bf{P} = P^\alpha\bf{g}_\alpha
$$

称参考矢量 $$\bf{g}^\alpha$$ 为**协变基矢量(covariant basis)**。

### 逆变基矢量
在同一平面内，存在唯一一组参考矢量 $$\bf{g}^\beta (\beta=1,2)$$ 满足对偶关系：

$$
\bf{g}^\beta \cdot \bf{g}_\alpha = \delta_{\alpha}^{\beta}
$$

式中 $$\delta_{\alpha}^{\beta}$$ 为Kronecker $$\delta_{\alpha}^{\beta}$$ 。当 $$\alpha=\beta$$ 时， $$\delta_{\alpha}^{\beta}=1$$ ，否则 $$\delta_{\alpha}^{\beta}=0$$ 。
并称参考矢量 $$\bf{g}^\beta$$ 为**逆变基矢量(contravariant basis)**。

记 $$\varphi = <\bf{g}_1,\bf{g}_2>$$ ，则

$$
|\bf{g}^1|=\frac{1}{|\bf{g}_1|sin(\varphi)}, \quad |\bf{g}^2|=\frac{1}{|\bf{g}_2|sin(\varphi)}
$$

### 矢量的分量
任意矢量 $$\bf{P}$$ 对协变基矢量 $$\bf{g}_\alpha$$ 分解的分量 $$P^\alpha$$ 称为矢量 $$\bf{P}$$ 的**逆变分量**：

$$
\bf{P} \cdot \bf{g}^\beta = P^\alpha\bf{g}_\alpha \cdot \bf{g}^\beta = P^\alpha \delta_{\alpha}^{\beta} = P^\beta
$$

任意矢量 $$\bf{P}$$ 对逆变基矢量 $$\bf{g}^\beta$$ 分解的分量 $$P_\beta$$ 称为矢量 $$\bf{P}$$ 的**协变分量**：

$$
\bf{P} \cdot \bf{g}_\alpha = P_\beta\bf{g}^\beta \cdot \bf{g}_\alpha = P_\beta \delta_{\alpha}^{\beta} = P_\alpha
$$

可以观察出，各个量的标记规律为：**下标为协变（矢量/分量），上边为逆变（矢量/分量）**。

## 三维空间中的斜角直线坐标系
### 协变基矢量
本部分考虑三维空间问题。在空间中可以选出任意一组线性无关的矢量 $$\bf{g}_i (i=1,2,3)$$ 作为参考矢量，则空间中任意一点的位置可以用坐标原点到该点的矢径 $$\bf{r}$$ 表示：

$$
\bf{r} = x^i \bf{g}_i = x^1 \bf{g}_1 + x^2 \bf{g}_2 + x^3 \bf{g}_3
$$

由上式可得矢径对坐标 $$x^i$$ 的微分：

$$
d\bf{r} = \frac{\partial \bf{r}}{\partial x^i} dx^i = \bf{g}_i dx^i
$$

并将矢径对坐标的偏导数 $$\bf{g}_i$$ 定义为**协变基矢量**，成为**自然基矢量**，即

$$
\bf{g}_i = \frac{\partial \bf{r}}{\partial x^i}
$$

### 逆变基矢量
与平面问题类似，由对偶关系可以得到唯一一组与协变基矢量 $$\bf{g}_i$$ 对应的逆变基矢量 $$\bf{g}^j (j=1,2,3)$$ ：

$$
\bf{g}^j \cdot \bf{g}_i = \delta_i^j
$$

### 由协变基矢量求逆变基矢量
#### 方法一
因 $$\bf{g}^1$$ 垂直于 $$\bf{g}_2$$ 与 $$\bf{g}_3$$ ，可令 $$\bf{g}^1=a\bf{g}_2 \times \bf{g}_3$$ 。又因 $$\bf{g}^1 \cdot \bf{g}_1 = 1$$ 可得：

$$
1 = \bf{g}^1 \cdot \bf{g}_1 = a(\bf{g}_2 \times \bf{g}_3) \cdot \bf{g}_1
$$

对固定的协变基矢量 $$\bf{g}_i$$，混合积 $$(\bf{g}_2 \times \bf{g}_3) \cdot \bf{g}_1$$ 为固定常数，可以由上式求的 $$a$$ 。
同理可求 $$\bf{g}^2$$ 与 $$\bf{g}^3$$ 。

#### 方法二
将逆变基矢量 $$\bf{g}^i$$ 对协变基 $$\bf{g}_j$$ 进行分解，即：

$$
\bf{g}^i = g^{ij} \bf{g}_j
$$

由对偶关系可知

$$
\bf{g}^i \cdot \bf{g}^j = g^{ik} \bf{g}_k \cdot \bf{g}^j = g^{ik} \delta_k^j = g^{ij}
$$

同理，协变基矢量 $$\bf{g}_i$$ 可以对逆变基矢量 $$\bf{g}^j$$ 分解：

$$
\bf{g}_i = g_{ij} \bf{g}^j
$$

且有

$$
\bf{g}_i \cdot \bf{g}_j = g_{ij}
$$

称 $$g_{ij}$$ 为**度量张量的协变分量**， $$g^{ij}$$ 为**度量张量的逆变分量**。

下面对 $$g_{ij}$$ 与 $$g^{ij}$$ 进行一些讨论。
* 由矢量内积的交换律可知 $$g_{ij} = g_{ji}$$ ，$$g^{ij} = g^{ji}$$ ，即由 $$g_{ij}$$ 与 $$g^{ij}$$ 各自构成的矩阵 $$[g_{ij}]$$ 与 $$[g^{ij}]$$ 为对称矩阵：

$$
[g_{ij}] = [g_{ij}]^T, \quad [g^{ij}] = [g^{ij}]^T
$$

其中，矩阵元素的前指标表示行号，后指标表示列号。

* 由对偶关系可知：

$$
\delta_i^j = \bf{g}_i \cdot \bf{g}^j = g_{ik} \bf{g}^k \cdot \bf{g}^j = g_{ik} g^{kj}
$$

即由 $$g_{ij}$$ 与 $$g^{ij}$$ 各自构成的矩阵互逆:

$$
[g^{ij}] = [g_{ij}]^{-1}
$$

* 若协变基矢量 $$\bf{g}_i$$ 构成右手系，逆变基矢量 $$\bf{g}^j$$ 也构成右手系。

### 指标升降关系
与平面问题类似，任意矢量 $$\bf{P}$$ 既可以对协变基矢量分解，有可以对逆变基矢量分解

$$
\bf{P} = P^i \bf{g}_i = P_j \bf{g}^j
$$

且有

$$
P^i = \bf{P} \cdot \bf{g}^i = P_k \bf{g}^k \cdot \bf{g}^i = P_k g^{ki} \\
P_j = \bf{P} \cdot \bf{g}_j = P^k \bf{g}_k \cdot \bf{g}_j = P^k g_{kj}
$$

上述两式称为矢量分量的**指标升降关系**。

基矢量也有类似的指标升降关系:

$$
\bf{g}^i = g^{ij} \bf{g}_j \\
\bf{g}_i = g_{ij} \bf{g}^j
$$

可以发现，起升指标作用的是度量张量的逆变分量 $$g^{ij}$$ ，起降指标作用的是度量张量的协变分量 $$g_{ij}$$ 。度量张量的分量可以把需要升降的矢量/矢量分量的指标转变为相同位置的指标，即变换后的指标位置与度量张量的分量指标位置相同。

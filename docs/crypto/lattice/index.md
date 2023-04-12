# 简介

参考资料 [EECS 598](https://web.eecs.umich.edu/~cpeikert/lic15/) [Lectures](https://github.com/cpeikert/LatticesInCryptography/)

## 什么是网格？

**Definition（Lattice）** 一个 $n$ 维的网格 $\mathcal{L}$ 是 $\mathbb{R}^n$ 的一个离散的加法子群.

## 网格的一些性质

**Theorem（Minkowski）** 令网格 $\mathcal{L}\in\mathbb R^n$，对于凸的、中心对称的图形 $S$，若它的体积 $\text{vol}(S)> 2^n\det(\mathcal{L})$，则 $S$ 至少包含一个非零网格点，即 $S\cup\mathcal{L}\neq\{0\}$.

**Corollary（Minkowski's First Theorem）** 对于任何网格 $\mathcal{L}$，都有 $\lambda_1(\mathcal L)\leq\sqrt{n}\det(\mathcal L)^{\frac1n}$.

## SVP 问题（Shortest Vector Problem）

**定义（SVP问题）** 不失一般性地，我们只讨论整数网格（虽然我不知道为什么不失一般性）。SVP问题有三种形式：

- Decision 给定网格基 $B$ 和一个实数 $d$，判断 $\lambda_1(\mathcal{L}(B))\leq d$ 还是 $\lambda_1(\mathcal{L}(B))>d$.
- Calculation 给定网格基 $B$，计算 $\lambda_1(\mathcal{L}(B))$.
- Search 给定网格基 $B$，找到一个 $v\in\mathcal{L}(B)$ 使得 $||v||=\lambda_1(\mathcal{L}(B))$.

容易看到 Decision $\leq$ Calculation $\leq$ Search.（这里 $\leq$ 表示归约）

Calculation 可以通过 Decision + 二分查找得到，因此 Calculation $\leq$ Decision.需要注意的一点是，$(\lambda_1(\mathcal{L}(B)))^2$ 是一个整数，而由`Minkowski’s First Theorem`，$\lambda_1(\mathcal{L}(B))<\sqrt{n}\det(\mathcal{L(B)})^{\frac1n}=2^{\text{poly}(|B|)}$，因此这个归约是成立的.

事实上同样有 Search $\leq$ Calculation（现在先不讨论），因此三个问题是等价的.
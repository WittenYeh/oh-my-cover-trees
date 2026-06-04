# (Cover Tree) ICML06: Cover Tree for Nearest Neighbor

## 基本知识和符号

### Doubling Dimension

设 $S$ 是度量空间 $(X, d)$ 中的一个点集。对任意点 $p \in X$ 与半径 $r > 0$，记

$$B_S(p, r) = \{\, q \in S \mid d(p, q) \le r \,\}$$

为以 $p$ 为中心、$r$ 为半径的**闭球内属于 $S$ 的点集**，$|B_S(p, r)|$ 表示该点集中点的个数。

$S$ 的 **doubling constant** 是满足下述性质的最小值 $c$：任意球 $B_S(p, r)$ 都可被 $c$ 个半径减半的球 $B_S(\cdot, r/2)$ 覆盖。$S$ 的 **doubling dimension** 定义为

$$\dim_{KL}(S) = \log c,$$

其中下标 KL 表示 Krauthgamer & Lee [2]。直观上 $\dim_{KL}$ 把欧氏维数推广到一般度量空间：若 $S$ 大致均匀分布在某个 $d$ 维曲面上，则 $c \sim 2^d$，从而 $\dim_{KL}(S) \approx d$。如 Gupta et al. [4] 所证，该概念严格地比由 expansion constant 定义的 KR-dimension（见下）更 general。

### Expansion Constant

**定义（expansion constant）.** 点集 $S$ 的 expansion constant 是满足下式的最小实数 $c \ge 2$：

$$|B_S(p, 2r)| \le c \cdot |B_S(p, r)|, \qquad \forall\, p \in X,\ \forall\, r > 0.$$

即：把查询半径加倍时，落入球内的点数至多增大为原来的 $c$ 倍。它是 Karger–Ruhl [3] 提出的增长受限度量（growth-restricted metric）常数，可视为 doubling dimension 的离散计数版类比；由此定义的 **KR-dimension（expansion dimension）** 为

$$\dim_{KR}(S) = \log c.$$

cover tree [1] 的分析主要基于 expansion constant $c$，其构建与查询的 worst time complexity 均以 $c$ 表述。

## 参考文献

- [1] A. Beygelzimer, S. Kakade, J. Langford. *Cover Trees for Nearest Neighbor.* ICML 2006, pp. 97–104.
- [2] R. Krauthgamer, J. R. Lee. *Navigating Nets: Simple Algorithms for Proximity Search.* SODA 2004, pp. 798–807.
- [3] D. R. Karger, M. Ruhl. *Finding Nearest Neighbors in Growth-Restricted Metrics.* STOC 2002, pp. 741–750.
- [4] A. Gupta, R. Krauthgamer, J. R. Lee. *Bounded Geometries, Fractals, and Low-Distortion Embeddings.* FOCS 2003, pp. 534–543.
- [5] Y. Elkin, V. Kurlin. *A New Near-linear Time Algorithm for k-Nearest Neighbor Search Using a Compressed Cover Tree.* ICML 2023.

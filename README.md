# Oh My Cover Trees!

## Awesome Cover Trees

A curated overview of the cover-tree line of work, as surveyed in
*A New Near-linear Time Algorithm for k-Nearest Neighbor Search Using a
Compressed Cover Tree* (Elkin & Kurlin, ICML 2023). The table collects the
key papers in the cover-tree lineage — those that introduce, implement, extend,
or fix the proofs of cover trees for nearest-neighbor search in metric spaces.

| Year | Work | Paper | Key contribution | Query time |
|------|------|-------|------------------|------------|
| 2006 | Beygelzimer, Kakade & Langford (ICML) | [Cover Trees for Nearest Neighbor](paper-pdfs/%28Cover%20Tree%29%20ICML06%20-%20Cover%20Trees%20for%20Nearest%20Neighbor.pdf) | Introduced the cover tree on a reference set `R`; claimed near-linear build and $O(c(R)^{12}\log\lvert R\rvert)$ NN search | $O\left(c(R)^{12}\log\lvert R\rvert\right)$ ($k=1$) |
| 2006 | Beygelzimer, Kakade & Langford | [Cover Trees for Nearest Neighbor (Extended Version)](paper-pdfs/%28Cover%20Tree%2C%20Extended%29%20TR06%20-%20Cover%20Trees%20for%20Nearest%20Neighbor%20%28Extended%20Version%29.pdf) | Extended version of the ICML paper; using cover trees on both query set `Q` and reference set `R` | — |
| 2006 | Kollár | Fast Nearest Neighbors (CSAIL Tech. Report — no public PDF) | Probabilistic NN algorithm; corrected pseudo-code of the cover-tree construction | — |
| 2009 | Ram, Lee, March & Gray (NIPS) | [Linear-time Algorithms for Pairwise Statistical Problems](paper-pdfs/%28Dual-Tree%29%20NIPS09%20-%20Linear-time%20Algorithms%20for%20Pairwise%20Statistical%20Problems.pdf) | Dual-tree `k`-NN using cover trees on `Q` and `R` | — |
| 2015 | Curtin, Lee, March & Ram (JMLR) | [Plug-and-Play Dual-Tree Algorithm Runtime Analysis](paper-pdfs/%28Dual-Tree%29%20JMLR15%20-%20Plug-and-Play%20Dual-Tree%20Algorithm%20Runtime%20Analysis.pdf) | Dual-tree `k`-NN on `Q` and `R`; also pointed out (Section 5.3) a crucial gap in the proof of Beygelzimer et al. (2006a, Thm 5) | — |
| 2015 | Izbicki & Shelton (ICML) | [Faster Cover Trees](paper-pdfs/%28Faster%20Cover%20Tree%29%20ICML15%20-%20Faster%20Cover%20Trees.pdf) | A new, more efficient implementation (no new complexity proofs) | — |
| 2016 | Jahanseir & Sheehy (CCCG) | [Transforming Hierarchical Trees on Metric Spaces](paper-pdfs/%28Net-Tree%29%20CCCG16%20-%20Transforming%20Hierarchical%20Trees%20on%20Metric%20Spaces.pdf) | Explored connections between cover trees and (modified navigating) net-trees | — |
| 2022 | Elkin & Kurlin (TopoInVis) | [Counterexamples Expose Gaps in the Proof of Time Complexity for Cover Trees Introduced in 2006](paper-pdfs/%28Counterexamples%29%20TopoInVis22%20-%20Counterexamples%20Expose%20Gaps%20in%20the%20Proof%20of%20Time%20Complexity%20for%20Cover%20Trees%20Introduced%20in%202006.pdf) | Counterexamples 4.2 / 5.2 showing the past proofs of Beygelzimer et al. (2006a, Thms 5 & 6) are incorrect | — |
| 2023 | **Elkin & Kurlin (ICML)** | [A New Near-linear Time Algorithm for k-Nearest Neighbor Search Using a Compressed Cover Tree](paper-pdfs/%28Compressed%20Cover%20Tree%29%20ICML23%20A%20New%20Near-linear%20Time%20Algorithm%20For%20k-Nearest%20Neighbor%20Search%20Using%20a%20Compressed%20Cover%20Tree.pdf) | Simpler tree (each point stored once); corrects the past gaps and proves near-linear build and `k`-NN search via the minimized expansion constant $c_m(R)$ | $O\left(\log k\left(c_m(R)^{O(1)}\log\lvert\Delta\rvert + \lvert\bar B(q, O(d_k(q,R)))\rvert\right)\right)$ |

### Complexity comparison (from the paper's Tables 1–4)

| Data structure | Build time | `k`-NN query time | Space | Proof status |
|----------------|-----------|-------------------|-------|--------------|
| Cover tree (Beygelzimer et al. 2006a) | $O\left(c(R)^{O(1)}\lvert R\rvert\log\lvert R\rvert\right)$ | $O\left(c(R)^{12}\log\lvert R\rvert\right)$ ($k=1$) | $O(\lvert R\rvert)$ | Shown incorrect by Elkin & Kurlin (2022a) |
| **Compressed cover tree (Elkin & Kurlin 2023)** | $O\left(c(R)^{O(1)}\lvert R\rvert\log\lvert R\rvert\right)$ | $O\left(c(R\cup\{q\})^{O(1)}\log k\,(\log\lvert R\rvert+k)\right)$ | $O(\lvert R\rvert)$ | Proved (Thms 3.7/3.10, 4.9; Cor. 3.11/4.7) |

**Key idea.** A *compressed* cover tree stores every point of `R` exactly once
(unlike the implicit cover tree with infinite repetitions, or the explicit
cover tree where a point appears at many levels). Combined with the *minimized
expansion constant* `c_m(R)`, this yields the first rigorous near-linear-time
proofs for both construction and `k`-nearest-neighbor search.

### Source papers

The PDFs surveyed here live under [`paper-pdfs/`](paper-pdfs/):
- *Cover Trees for Nearest Neighbor* — Beygelzimer, Kakade & Langford, ICML 2006.
- *A New Near-linear Time Algorithm for k-Nearest Neighbor Search Using a Compressed Cover Tree* — Elkin & Kurlin, ICML 2023 ([arXiv:2111.15478](https://arxiv.org/abs/2111.15478)).

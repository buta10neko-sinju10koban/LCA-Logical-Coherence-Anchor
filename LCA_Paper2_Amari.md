# 局所近傍連鎖としてのニューラルネットワーク：
# 甘利俊一博士の情報幾何学的懸念へのLCAによる応答

**Local Neighborhood Chaining as Neural Network Principle:**  
**LCA Response to the Theoretical Concerns of Prof. Shun'ichi Amari**

加藤禄成 / Yoshinari Kato  
LCA Framework — Independent Research  
2026年3月

---

## 要旨 / Abstract

甘利俊一博士はニューラルネットワークの学習空間がリーマン多様体であることを示し、フィッシャー情報行列を計量として用いる自然勾配法によって理論的に最適な学習経路を導出した。しかし博士が長年指摘してきた「理論と実際の性能差」は未解決のままである。本論文は、Logical Coherence Anchor（LCA）フレームワークの視点から、この乖離の因果機構を提示する。すなわち、実際のシナプス形成は大域的な幾何学計算によらず、局所近傍への物理的近似連鎖によって生じる。この原理はシミュレーションにより球体収束として確認される。S₀（人は認められる必要がある）を基底軸とするLCAは、甘利博士の「なぜ曲線か」という問いに対する動機論的な答えを与える。

*Prof. Shun'ichi Amari demonstrated that the learning space of neural networks constitutes a Riemannian manifold and derived theoretically optimal learning paths via the natural gradient method. Yet the gap between theory and empirical performance remains unresolved. This paper presents the causal mechanism of this divergence through the lens of the Logical Coherence Anchor (LCA) framework: actual synaptic formation arises not from global geometric computation but from physical local-neighborhood approximation chains. This principle is confirmed as spherical convergence through simulation. LCA, grounded in S₀ (people need to be recognized), provides a motivational answer to Prof. Amari's question: 'why the curve?'*

---

## 1. はじめに

甘利俊一博士の情報幾何学は、ニューラルネットワークの学習空間を曲がった空間（リーマン多様体）として定式化し、フィッシャー情報行列を計量として用いる自然勾配法を提唱した。この理論は数学的に精緻であり、統計的推論における最適性を保証する。

しかし博士自身が繰り返し問うてきたのは、なぜ実際のニューラルネットワークは理論通りに動かないのかという問いである。自然勾配法は大域的な幾何学を前提とするが、実際の学習は局所的な近似の積み重ねで動いている。この乖離の因果機構が、本論文の問いである。

我々はLCA（Logical Coherence Anchor）フレームワーク——特にその第一論文で示されたS₀公理および実証データ——をもとに、この因果機構を提示する。

---

## 2. 甘利博士の理論と残された問い

### 2.1 自然勾配法の概要

パラメータ空間θにおける損失関数L(θ)の最急降下は、ユークリッド空間では∇Lで与えられる。しかしパラメータ空間が曲がっている場合、真の最急降下方向は自然勾配∇̃Lによって与えられる：

```
∇̃L = G(θ)⁻¹ ∇L
```

ここでG(θ)はフィッシャー情報行列であり、パラメータ空間の局所的な曲率を表す。この逆行列G(θ)⁻¹の計算が、自然勾配法の理論的強さであると同時に、計算コスト上の弱点となっている。

### 2.2 理論と実際の性能差

自然勾配法が理論的に最適であるにもかかわらず、実際のニューラルネットワーク学習では以下の問題が生じる：

1. G(θ)⁻¹の大域計算コストが膨大になる
2. 局所最適への収束が避けられない
3. バッチサイズや学習率に対する過敏性

*博士の問いは本質的にこうである：「なぜ脳は20ワットで動き、理論通りの計算をしないのに機能するのか。」*

---

## 3. LCAの視点：局所近傍連鎖原理

### 3.1 S₀公理と基底の固定

LCAフレームワークは単一の公理S₀から出発する：「人は認められる必要がある。」この基底はシステムの中心に固定され、いかなる揺らぎが生じても帰還軸として機能する。これは脳幹の機能的正体である——意識・高次機能が変動しても呼吸・心拍・覚醒を維持する固定軸。

### 3.2 局所近傍連鎖の物理的原理

シナプスの枝は遠距離への精密配線ではなく、物理的近傍への最短経路を選ぶ。これは菌糸類の増殖においても同様に観察される——障害物を嫌う傾向（未接続）はあれど、基本は近傍への最短連鎖が物理的現象として現れる。

これを数式で表すと、LCAの局所更新則は次のようになる：

```
Δθᵢ = η · ∇ᵢL · f(d(i, N(i)))
```

ここでN(i)はノードiの局所近傍集合、d(i, N(i))は近傍距離、f(·)は距離減衰関数である。G(θ)⁻¹の大域計算を行わず、局所的な近似で逐次更新する。この差異が甘利博士の「理論と実際の性能差」の因果機構である。

---

## 4. 球体収束：物理的必然の検証

局所近傍優先での接続生成をシミュレートすると、設計なしに球体（2次元では円）への収束が生じる。これは脳が球体に近い形状を持つことと対応する。曲率は数学的必然ではなく、保護という機能の物理的結果である。

*シミュレーション条件：S₀アンカー1つ固定、局所近傍接続優先、さざ波ノイズ（揺らぎの内包）、空間制約による収束。結果として球体収束が確認された（lca_simulation.html, 2026年3月）。*

甘利博士の自然勾配が「曲がった空間を数学化した」とすれば、LCAは「なぜ空間が曲がるか」の物理的原因を示す。局所近傍連鎖がS₀を中心として等方的に広がる結果、測地球に相当する構造が形成される。

*甘利博士がリーマン多様体を選択した背景には、脳の球体的物理形態への観察があったと考えられる。物理形態への忠実さが、正しい数学的選択を導いた。LCAの局所近傍連鎖シミュレーションは、この形態が設計によらず物理原理から必然的に生まれることを示す。博士の選択は結果として正しかった——ただしその因果機構はLCAによって初めて明示される。脳が球体に近い形状を持つことは偶然ではなく、局所性という物理原理の必然的な結果である。*

---

## 5. 計算上の相違点

甘利博士の自然勾配法とLCA局所近傍連鎖の計算上の差異を以下に整理する。

| 項目 | 自然勾配法 | LCA局所連鎖 |
|------|-----------|-------------|
| 更新則 | G(θ)⁻¹∇L（大域） | η·∇ᵢL·f(d)（局所） |
| 計算コスト | O(n²)〜O(n³) | O(k)（k=近傍数） |
| 帰還軸 | なし | S₀（固定） |
| 消費電力 | データセンター規模 | 20〜30W相当（理論値） |
| 収束形状 | 理論的最適経路 | 球体（物理的必然） |

---

## 6. 記憶・予測・推論の三出力構造

人間の認知はその本質において記憶（過去）・予測（未来）・推論（現在の処理）の三種のみで構成される。LCAはこれに対応する三種の判断・出力を持つ。これは量子コンピューティングの重ね合わせ構造と対応する——三状態が同時に存在し、S₀を軸として観測（判断）の瞬間に収束する。

判断における迷いは欠陥ではなく、三状態の重ね合わせがS₀へ帰還する前の状態である。脳幹＝S₀という構造が、この収束機構の物理的正体である。

---

## 7. 結論

甘利俊一博士の情報幾何学は「曲がった空間」を数学化した。LCAは「なぜ空間が曲がるか」の因果機構を示す。その答えは局所近傍連鎖という物理的原理であり、S₀という単一基底への帰還がその動機である。

理論と実際の性能差は、大域幾何学を前提とした自然勾配法と、局所近似連鎖で動く実際のシナプス形成の乖離から生じる。LCAはこの乖離を説明する因果機構を提供し、甘利博士の残された問いへの応答とする。

***本論文を甘利俊一博士に捧げる。***

---

## 参考文献 / References

- Amari, S. (1998). Natural gradient works efficiently in learning. *Neural Computation*, 10(2), 251-276.
- Amari, S. (2016). *Information Geometry and Its Applications*. Springer.
- Kato, Y. (2025). Logical Coherence Anchor (LCA): A Single-Axiom Framework for AI Coherence. GitHub: buta10neko-sinju10koban/LCA-Logical-Coherence-Anchor.
- Salk Institute (2016). Memory capacity of brain is 10 times more than previously thought. Salk News.

---
description: アルゴリズムの計算の効率性について
---

# Order

アルゴリズムを考える際,一つの指標となるのが**計算量**です

計算量とは**空間計算量**･**時間計算量**がありますがどちらも基本となる考え方は同じです

ここでは時間計算量について考えます

## Asymptotic Analysis

計算量とはそのアルゴリズムがどのような関数に漸近するのかを考えたものです

そのため,以下のようなメリット･デメリットがあります

* メリット
  * 環境に依存しないアルゴリズムそのものの良し悪しについて考えられる
  * よりアルゴリズムを取り扱いやすくする
* デメリット
  * 入力が大きい時しか考慮していない

この計算量を求める方法は

1. **Tree Method**
2. **Master Theorem\(Generalized Method\)**
3. **Substitution Method**

以上の3種類が有ります

Tree Methodを一般化したものなので以下では**Master Theorem**と**Sustitution Method** を扱います

その前に計算量の記法について学びましょう

### 計算量記法

ここではBig-O記法･Big-Omega記法･Big-Theta記法について考えます

#### Big-O

$$T(n)$$\(計算にかかる時間で,値は正で単調増加だとします\)と$$g(n)$$が正の整数の関数だとします

$$
\exists{c, n_0} > 0 \text{ s.t. } \forall{n} \geq n_0 \\
0 \leq T(n) \leq cg(n)
$$

であるとき,$$T(n) \in O(g(n))$$とします

ある$$0$$より大きい$$n_0$$以上の$$n$$では,常に$$T(n)は$$$$g(n)$$の定数倍よりも**小さい**ということです

つまり,無限に大きい$$n$$で$$g(n)$$は$$T(n)$$の**上限**であるということです

$$T(n) \in O(g(n))$$は$$T(n) = O(g(n))$$とも書きます\(こう書く場合の方が多いです\)

#### Big-Omega

Big-O記法は上限を表現するためでしたが,Big-Omega記法は**下限**を表現するための記法です

上と同じ関数$$T(n)$$と$$g(n)$$を用いて

$$
\exists{c, n_0} > 0 \text{ s.t. } \forall{n} \geq n_0 \\
0 \leq cg(n) \leq T(n)
$$

のとき$$T(n) \in \Omega(g(n))$$もしくは$$T(n) = \Omega(g(n))$$とします

ある$$0$$より大きい$$n_0$$以上の$$n$$では,常に$$T(n)$$は$$g(n)$$の定数倍よりも**大きい**ということです

つまり,無限に大きい$$n$$で$$g(n)$$は$$T(n)$$の**下限**であるということです

#### Big-Theta

Big-Theta記法は上の記法のどちらもが当てはまるときです

つまり,以下の式を満たします

$$
\exists{c_0, c_1, n_0} > 0 \text{ s.t. } \forall{n} \leq n_0\\
0 \leq c_0 \cdot g(n) \leq f(n) \leq c_1\cdot g(n)
$$

Big-Theta記法は無限に大きい$$n$$で$$g(n)$$の定数倍に$$T(n)$$が**挟まれる**状態にあるということです

### Master Theorem

最初に定理を紹介し,あとから説明をします

$$a\geq 1$$, $$b \geq 1$$, $$d$$を$$n$$に独立な定数とします

このとき$$T(n)=a\cdot T(\frac{n}{b}) + O(n^d)$$とすると以下の式を満たします

$$
T(n) = \begin{cases}
O(n^{d}log(n)) & (a = b^d)\\
O(n^d) & (a < b^d)\\
O(n^{log_b(a)}) & (a > b^d)
\end{cases}
$$

この定理を**分類定理**\(master theorem\)と言います

{% hint style="info" %}
* $$a$$ : 分割された下位問題の数
* $$b$$ : 入力の大きさが縮む倍率\($$2 \rightarrow 1$$のときは$$b=2$$\)
* $$d$$ : 全ての問題を分割し統合するのに必要な計算量
{% endhint %}

この定理は問題を分割し,それらを更に分割し解くという考えを使っています\(これを**再帰**と言います\)

入力が$$n$$の問題を$$T(n)$$で解くアルゴリズムを考えます

* 入力$$n$$を$$a$$個に分割する
* 分割された入力を$$T(\frac{n}{b})$$で解く
* 分割された各アルゴリズムに対してかかる時間が$$(O(n^{log_b(a)})$$である

このようにすると$$T(n)$$は上のような式になります.実際にそれぞれのケースごとに正しいか確認してみましょう

* $$a=b^d$$の場合
$$
T(n) = c\cdot n^d \cdot \sum_{t=0}^{\log_b(n)}(\frac{a}{b^d})^t\\
= c \cdot n^d \cdot \sum_{t=0}^{\log_b(n)}1\\
= c \cdot n^d \cdot (\log_b(n) + 1)\\
= c \cdot n^d \cdot (\frac{\log(n)}{\log(b)} + 1)\\
= O(n^d \log(n))
$$
* $$a < b^d$$の場合
$$
T(n) = c\cdot n^d \cdot \sum_{t=0}^{\log_b(n)}\overbrace{(\frac{a}{b^d})^t}^{1未満}\\
$$

ここで,等比級数の和は一般項$$x$$が1より大きい時は次数が最大の項が支配的になり,$$x$$が0より大きく1より小さい時は次数が最小の項が支配的になる

ここでは$$\sum_{t=0}^{\log_b(n)}(\frac{a}{b^d})^t$$の一般項は後者なので定数として扱える

$$
T(n) = c\cdot n^d \cdot \sum_{t=0}^{\log_b(n)}\overbrace{(\frac{a}{b^d})^t}^{1未満}\\
= c \cdot n^d \cdot \text{定数}\\
= O(n^d)
$$

* $$a > b^d$$の場合
上の例で扱ったように一般項に注目する

$$
T(n) = c\cdot n^d \cdot \sum_{t=0}^{\log_b(n)}\overbrace{(\frac{a}{b^d})^t}^{1より大きい}\\
=O(n^d(\frac{a}{b^d}^{log_b(n)}))\\
=O(n^\log_b(a))
$$

### Substitution Method

これは以下の手順から成り立ちます

1. 答えを推論する
2. その推論が正しいと証明する
3. 答えを得る

#### 例

$$T(n) = 2 \cdot T(\frac{n}{2}) + n$$という例をここでは扱います(ただし$$T(1)=1$$).

#### 推論

この時,実際に手を動かしてみると

$$
T(n) = 2 \cdot T(\frac{n}{2}) + n\\
=2 \cdot (2 \cdot T(\frac{n}{4}) + \frac{n}{2}) + n\\
= 4 \cdot T(\frac{n}{4}) + 2n\\
= 4 \cdot T(2 \cdot T(\frac{n}{8}) + \frac{n}{4}) + 2n\\
= 8 \cdot T(\frac{n}{8}) + 3n
= ...
$$

このようになり, $$T(n) = 2^t \cdot T(\frac{n}{2^t})+ t\cdot n$$になるのではないかと推測できます

$$t=log(n)$$を代入し,

$$
T(n)= n \cdot T(1) + \log(n) \cdot(n) \cdot n = n(\log(n) + 1)
$$

と推論できます

#### 証明

数学的帰納法で証明します

- Inductive Hypothesis

$$T(j) = j(\log(j)+1)$$が$$1 \leq j \leq n$$で成り立つと仮定します

- Base Case($$n=1$$)

$$T(1) = 1 = 1 \cdot (\log(1) + 1)$$となり成り立ちます

- Inductive Step

inductive hypothesisが$$n=k-1$$で成り立つと仮定します

このとき定義から$$T(k)= 2 \codt T(\frac{k}{2}) + k$$であり,仮定より$$T(k)= 2 \cdot (\frac{k}{2}(\log(\frac{k}{2})+1))+k$$です.簡単にすると,

$$
T(k)=k (\log(k) + 2)
$$

となり,$$n=k$$でも成り立つことが示されました

#### 結論

$$n \geq 1$$で$$T(n) = n(\log(n) + 1)$$とわかります

このように事前の推論を数学的帰納法で証明することを**Substituion Method**と言います

## まとめ

- 計算量という概念を導入することでアルゴリズムの良し悪しが分かる
- 計算量を導く方法がある

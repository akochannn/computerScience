---
description: 情報量とエントロピーについて
---

# Entropy

### 情報量の定義

情報を知識を｢不確実｣なものから｢確実｣なものへとするものと定義します

その際

$$
\text{情報量} = \text{不確実さ}
$$

と式で表せます

事象が$$n$$個あり,その中から$$1 \leq i \leq n$$として$$A_i$$が起きるのを知らせる情報量を求める関数を$$f(n)$$とします

$$n$$個が大きいほど,どの事象が起こったのか見当がつきにくいので$$f(n)$$は大きくなります

また,｢$$n$$個の事象を$$k$$個ずつ$$m$$組に分けて,その$$m$$組の中から1つを選ぶ,その組の$$k$$個の中から1つを選ぶ｣場合と｢直接$$n(=m+k)$$個の事象から1つを選ぶ｣場合で得られる情報量は同じです.

つまり

$$
f(mk) = f(m) + f(k)
$$

が成り立ちます

これを**情報の加法性**と言います

#### ビット

ここで$$f(xy)=f(x)+f(y)$$とすると

$$
f(x + \varepsilon x) = f\{(1 + \varepsilon)x\}\\
= f(1 + \varepsilon) + f(x)
$$

よって

$$
\frac{f(x+\varepsilon x) - f(x)}{\varepsilon x} = \frac{f(1+\varepsilon)}{\varepsilon x} \tag{1}
$$

$$\varepsilon \to 0$$とすると左辺は明らかに$$f(x)$$の導関数$$f'(x) $$であり,



$$
\lim_{\varepsilon \to \infty} \frac{f(1 + \varepsilon)}{\varepsilon} = c
$$

とするとこれを変形して

$$
\lim_{\varepsilon \to 0} \frac{f(1 + \varepsilon)}{\varepsilon x} = \frac{c}{x}
$$

であり$$(1)$$から左辺は$$f'(x)$$だから

$$
f'(x) = \frac{c}{x}
$$

という微分方程式を得る

$$
f(x) = c\log(x) + d \;\;\;(\log = \log_e)
$$

となる

$$n=1$$のとき$$f(1)=0$$であるから$$d=0$$

YES or Noで決まるような二者択一の情報量の単位を1**ビット\(bit, binary digit\)**とすると

$$
f(2) = 1\text{bit}
$$

よって$$f(x)=c\log(x)$$に代入して

$$
f(2) = c\log_e 2 = 1
$$

つまり

$$
c \cdot \frac{\log_2 2}{\log_2 e} = 1
$$

よって

$$
c = \log_2 e
$$

以上より$$f(x) =\log_2 x \text{ bit}$$

また以降対数の底は$$2$$とする


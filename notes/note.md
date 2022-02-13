# Learning Programming Bitcoin

## 1章: 有限体

### 集合体の定義

* a + b, a * b が集合内に存在する = 閉じている
* a + 0 = a となる 0 が集合内に存在する
  * この 0 が加法単位元
* a * 1 = a となる 1 が集合内に存在する
  * この 1 が乗法単位元
* a + (-a) = 0 となる -a が集合内に存在する
  * この -a が加法逆元
* a * a^-1 = 1 となる a^-1 が集合内に存在する
  * この a^-1 が乗法逆元
* 体の位数は必ず素数の冪

### モジュロ演算

```text
7 % 3 = 1
```

### 有限体の加算と減算

* 有限体の加算を +f と表現
* 有限体の減算を -f と表現

位数が19の有限体 => F19 = {0, 1, ... 18}


```text
7 +f 8 = (7 + 8) % 19 = 15

11 -f 9 = (11 - 9) % 19 = 2
```

### 有限体の乗算とべき計算

* 有限体の加算を *f と表現

```text
5 *f 3 = 5 +f 5 +f 5 = 15 % 19 = 15

7^3 = 343 % 19 = 1
```

### 有限体の除算

* 有限体の加算を /f と表現

除算は乗算の逆算

通常の数学

* 7 * 8 = 56 は 56 / 8 = 7 を表す

集合体の場合

* `3 *f 7 = 21 % 19 = 2` は `2 /f 7 = 3` を表す
* `9 *f 5 = 45 % 19 = 7` は `7 /f 5 = 9` を表す

### フェルマーの小定理

p を素数とし、a を p の倍数でない整数（a と p は互いに素）とするときに、

<img src="https://latex.codecogs.com/svg.image?{\displaystyle&space;a^{p-1}\equiv&space;1{\pmod&space;{p}}}{\displaystyle&space;a^{p-1}\equiv&space;1{\pmod&space;{p}}}" title="{\displaystyle a^{p-1}\equiv 1{\pmod {p}}}{\displaystyle a^{p-1}\equiv 1{\pmod {p}}}" />

すなわち、a の p − 1 乗を p で割った余りは 1 であるというもの。

[フェルマーの小定理 - Wikipedia](https://ja.wikipedia.org/wiki/%E3%83%95%E3%82%A7%E3%83%AB%E3%83%9E%E3%83%BC%E3%81%AE%E5%B0%8F%E5%AE%9A%E7%90%86)

```text
n^(p-1) % p = 1
```

[合同式(mod)の意味とよく使う６つの性質 | 高校数学の美しい物語](https://manabitimes.jp/math/683)

[フェルマーの小定理の証明と例題 | 高校数学の美しい物語](https://manabitimes.jp/math/680)

## 2章: 楕円曲線

### 定義

<img src="https://latex.codecogs.com/svg.image?{\displaystyle&space;y^{2}=x^{3}&plus;ax&plus;b}" title="{\displaystyle y^{2}=x^{3}+ax+b}" />

```text
y^2 = x^3 + a*x + b
```

#### secq256k1

```text
y^2 = x^3 + 7
```

<img src="https://latex.codecogs.com/svg.image?{\displaystyle&space;y^{2}=x^{3}&plus;7}" title="{\displaystyle y^{2}=x^{3}+7}" />

### 点の加算

> 楕円曲線E上に位置する2点 <img src="https://latex.codecogs.com/svg.image?{\displaystyle P_{\!A}\,(x_{1},\,y_{1}),\,P_{\!B}\,(x_{2},\,y_{2})}P_{{\!A}}\,(x_{1},\,y_{1}),\,P_{{\!B}}\,(x_{2},\,y_{2})"> の加算は以下の通りである。
>
> まず、無限遠点を <img src="https://latex.codecogs.com/svg.image?{\displaystyle O}"> とすると、 <img src="https://latex.codecogs.com/svg.image?{\displaystyle P_{\!A}+O=O+P_{\!A}=P_{\!A}}"> である。すなわち、 <img src="https://latex.codecogs.com/svg.image?{\displaystyle O}"> が単位元である。
>
> もし <img src="https://latex.codecogs.com/svg.image?{\displaystyle x_{1}=x_{2},y_{1}=-y_{2}}"> ならば、<img src="https://latex.codecogs.com/svg.image?{\displaystyle P_{\!A}+P_{\!B}=O}"> である。
>
>
> それ以外の場合、<img src="https://latex.codecogs.com/svg.image?{\displaystyle P_{\!C}=P_{\!A}+P_{\!B}}P_{{\!C}}=P_{{\!A}}+P_{{\!B}}"> は、2点 <img src="https://latex.codecogs.com/svg.image?{\displaystyle P_{\!A},\,P_{\!B}}P_{{\!A}},\,P_{{\!B}}"> を通る直線とEとの（<img src="https://latex.codecogs.com/svg.image?{\displaystyle P_{\!A}}P_{{\!A}}"> および <img src="https://latex.codecogs.com/svg.image?{\displaystyle P_{\!B}}P_{{\!B}}"> と異なる）交点の、y座標の符号を反転したものである。すなわち <img src="https://latex.codecogs.com/svg.image?{\displaystyle P_{\!C}\,(x_{3},\,y_{3})}P_{{\!C}}\,(x_{3},\,y_{3})"> は以下のようになる。
>
> <img src="https://latex.codecogs.com/svg.image?{\displaystyle x_{3}=\phi ^{2}-x_{1}-x_{2},}">
>
> <img src="https://latex.codecogs.com/svg.image?{\displaystyle y_{3}=-\phi x_{3}-\psi .}">
>
> ただし <img src="https://latex.codecogs.com/svg.image?{\displaystyle \phi ,\,\psi }"> は
>
> <img src="https://latex.codecogs.com/svg.image?{\displaystyle \phi ={\frac {y_{2}-y_{1}}{x_{2}-x_{1}}},}">
>
> <img src="https://latex.codecogs.com/svg.image?{\displaystyle \psi ={\frac {y_{1}x_{2}-y_{2}x_{1}}{x_{2}-x_{1}}}.}">
>
> [楕円曲線暗号 - Wikipedia](https://ja.wikipedia.org/wiki/%E6%A5%95%E5%86%86%E6%9B%B2%E7%B7%9A%E6%9A%97%E5%8F%B7)

> と、言葉だけで説明するといまいち良く分からないですね。というか無限遠点って何だ。
>
> とりあえず無限遠点のことは置いといて、無限遠点じゃない点に関しての加法演算を視覚化してみます。
>
> <img class="aligncenter size-full wp-image-79296" src="https://techracho.bpsinc.jp/wp-content/uploads/2019/08/elliptic_curve_additive_group.png" alt="" width="300">
>
> P と Q を通る直線と楕円曲線の新たな交点の y 座標を反転した点 R' が一意に定まることが分かるでしょうか。
>
> 一方で、上図の R と R' のように、x軸に対称な2点に加法演算を適用した場合、直線と楕円曲線は新たな交点を作らないので、楕円曲線上の一意な点を作れません。このような場合に解なしとしてしまうと加算群が作れなくなってしまうので、無限遠点が導入されます。
>
> [楕円曲線暗号アルゴリズムを理解する｜TechRacho by BPS株式会社](https://techracho.bpsinc.jp/yoshi/2019_08_16/79280)

### 数学的解説

* 同一性
  * 単位元があること
  * A + I = Aとなる点Iが存在する
  * この点を *無限遠点* と呼ぶ
* 可換性
  * A + (-A) = I
* 結合性
  * A + B = B + A
* 可逆性
  * (A + B) + C = A + (B + C)

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

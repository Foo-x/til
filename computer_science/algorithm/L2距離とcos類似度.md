# L2距離とcos類似度

2つのベクトルの「近さ」を計算する方法のうち、L2距離（ユークリッド距離）とcos類似度がよく使われる。

ベクトルAとBがあるとき、それぞれ以下のように計算できる。

```
L2距離 = || A - B || ^ 2

cos類似度 = AB / ||A|| ||B||
```

L2距離はベクトルの各要素の大きさ、cos類似度はベクトルの角度に意味があるときに使う。

# transformプロパティでアニメーションさせるメリット

要素をアニメーションさせるとき、位置であれば `top/left`、大きさであれば `width/height` を直接アニメーションさせることもできる。  
しかし、`transform` でアニメーションさせたほうが良い。  
メリットは以下の通り。

- レイアウトに影響を与えないので、他の要素がずれたりしない
- GPUで描画されるのでパフォーマンスが良い
- 動きがなめらかになる
    - `top/left` や `width/height` は1ピクセル単位で動くので、カクカクになる
    - `transform` は1ピクセル未満の変換にも対応しているのでなめらか

参考

- [Why moving elements with translate() is better than pos:abs top/left - Paul Irish](https://www.paulirish.com/2012/why-moving-elements-with-translate-is-better-than-posabs-topleft/)

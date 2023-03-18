# CSS封じ込め

CSSの `contain` プロパティを使うと、要素が変更されたときに他の要素を再描画するかどうかを制御できる。  
つまり、要素の変更をその要素のみに「封じ込め」ることができて、パフォーマンスが向上する。

設定できる値は以下の通り。

- `size`
    - 要素の大きさを封じ込める
    - width/height を指定しないと大きさが0として扱われるので注意
- `layout`
    - 要素の配置を封じ込める
- `paint`
    - 要素の表示を封じ込める
    - 要素外に子要素が描画されなくなる
- `style`
    - 要素のプロパティを封じ込める
    - カウンターの値など
- `none`
    - 封じ込めない
- `strict`
    - `size layout paint` と同等
- `content`
    - `layout paint` と同等

大きさが動的な場合は `content`、固定の場合は `strict` を使うのが良い。

また、関連するプロパティとして `content-visibility` がある。  
`auto` という値を設定すると、表示領域外で描画されなくなり、パフォーマンスが向上する。  
その際、`contain-intrinsic-size` に大きさを指定すると、表示領域外でも大きさは確保される。

参考

- [contain - CSS: カスケーディングスタイルシート | MDN](https://developer.mozilla.org/ja/docs/Web/CSS/contain)
- [content-visibility - CSS: カスケーディングスタイルシート | MDN](https://developer.mozilla.org/ja/docs/Web/CSS/content-visibility)
- [表示速度を飛躍的に向上させるHTML/CSS最新仕様「content-visibility」「Lazy loading」「contain」をコード付き簡単解説 - Yahoo! JAPAN Tech Blog](https://techblog.yahoo.co.jp/entry/2020090830016393/)
- [CSSの新しいプロパティ「content-visibility」レンダリングのパフォーマンスが向上する | コリス](https://coliss.com/articles/build-websites/operation/css/css-new-property-content-visibility.html)

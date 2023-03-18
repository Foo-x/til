# is擬似クラス

`:is()` 擬似クラスは、受け取ったセレクタのいずれかにマッチするセレクタとして働く。  
たとえば以下のようにすることで簡潔に記述できる。

```css
/* :is() を使わない場合 */
.foo .xxx,
.bar .xxx,
.baz .xxx {
    // props
}

/* :is() を使う場合 */
:is(.foo, .bar, .baz) .xxx {
    // props
}
```

参考

- [:is() (:matches(), :any()) - CSS: カスケーディングスタイルシート | MDN](https://developer.mozilla.org/ja/docs/Web/CSS/:is)

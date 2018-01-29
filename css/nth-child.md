# :nth-child(n)について

`foo:nth-child(n)`は、n番目の要素がfooでない場合、対象の要素がないことになる。

例:
```html
<div>
  <foo/>
  <bar/>
  <foo/>
</div>
```

上のとき、`div foo:nth-child(2)`が適用される要素は存在しない。
nが1か3であれば存在する。
「2番目のfoo」を指定する場合は`div foo:nth-of-type(2)`のようにする。

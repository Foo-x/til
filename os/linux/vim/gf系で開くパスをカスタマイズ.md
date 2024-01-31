# gf系で開くパスをカスタマイズ

`includeexpr` を使うとgf系で取得したパスを変換できる。  
たとえば `setlocal includeexpr=substitute(v:fname,'\\.','/','g')` のようにすると、`foo.bar.baz` となっている部分を `foo/bar/baz` に変換してからgf系に渡せる。  
Javaなどで便利。

`path` を使うとgf系で探索するパスを変更できる。  
たとえば `setlocal path+=foo` のようにすると `foo` ディレクトリからの相対パスも探索される。  
指定できるパスのパターンは `:h file-searching` を参照。  
ワイルドカードの `*` `**` や、上向き検索の `;` がある。

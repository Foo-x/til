# wslviewのsyntax_error解消

wslviewで `1:932+0: syntax error in expression (error token is ":932+0")` のようなエラーが出て使えなくなることがある。  
`echo 65001 > ~/.config/wslu/oemcp` を実行すると直る。

`~/.config/wslu/oemcp` は文字コードを持っているファイルだが、何かしらの原因で `1:932` のような値が入ることがある様子。  
wslviewの中でその値を使って算術演算しているが、`:` が含まれるためエラーになる。  
UTFの文字コードである65001を設定することで直る。

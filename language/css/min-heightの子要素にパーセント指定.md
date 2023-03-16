# min-height の子要素にパーセント指定

親要素で `height` を指定せずに `min-height` のみを指定すると、子要素で `height: 100%` を指定しても `min-height` の値にならない。  
親要素の `height` に `min-height` より小さい任意の値を指定すると反映されるようになる。  
なお、`min-height` より大きい値を指定するとその値になる。

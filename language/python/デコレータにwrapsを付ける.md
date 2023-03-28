# デコレータにwrapsを付ける

デコレータとして返す関数には `functools.wraps` のデコレータを付ける。  
付けないと元の関数名やドキュメンテーションがデコレータのものになってしまうため。

[functools --- 高階関数と呼び出し可能オブジェクトの操作 — Python 3 ドキュメント](https://docs.python.org/ja/3/library/functools.html#functools.wraps)

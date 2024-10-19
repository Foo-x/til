# BackpressureとLoadShedding

受け取るデータ量が処理できる量を上回っている場合、バッファメモリに保持しておいて後で処理することで一時的なスパイクには対応できる。  
しかし、バッファメモリも枯渇するほど大量のデータを受け取った場合、最悪 out-of-memory でシステムが停止したり、データが損失したりする。  
それを防ぐために、枯渇しそうになった段階でエラーレスポンスを返す方法がある。  
その後、送信側でデータ量を調整する仕組みをBackpressure（バックプレッシャ―、背圧）、受信側で受け取ったデータを破棄する仕組みを Load Shedding（ロードシェディング、負荷制限）という。  
Backpressureによって負荷自体を減らすのが理想だが、送信側が不特定多数だったりすると制御できないため、Load Shedding によって少なくとも受信側がクラッシュしないようにする。

Backpressureはもともと流体力学で逆流を防ぐための圧力を指す言葉。  
Load Shedding は全体の停電を避けるために局所的な停電を起こす仕組みを指す言葉。  
それぞれ転じてシステム間における通信量の制御全般に使われるようになった。

参考

- [バックプレッシャーとは - IT用語辞典 e-Words](https://e-words.jp/w/%E3%83%90%E3%83%83%E3%82%AF%E3%83%97%E3%83%AC%E3%83%83%E3%82%B7%E3%83%A3%E3%83%BC.html)
- [Back Pressure - Awesome Software Architecture](https://awesome-architecture.com/back-pressure/)

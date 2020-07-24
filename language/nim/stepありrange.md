# stepありrange

`start..end..step`のような書き方はできない。  
`countup(start, end, step)`を使う。  
なお、これをseqにする場合、`countup(start, end, step).toSeq()`という書き方はできず、`toSeq(countup(start, end, step))`のようにする。

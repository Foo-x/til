# cmapやcabbrevをそのキーだけ入力されたときにのみ有効にする

たとえば `cmap f foo` とすると、`:f` だけでなく `echo f` のように他の入力がすでにあるときも実行される。  
前者だけ有効にしたいときは以下のようにする。

`cmap <expr> f getcmdtype() == ':' && empty(getcmdline()) ? 'foo' : 'f'`

cabbrevも同様。

`cabbrev <expr> f getcmdtype() == ':' && getcmdline() ==# 'f' ? 'foo' : 'f'`

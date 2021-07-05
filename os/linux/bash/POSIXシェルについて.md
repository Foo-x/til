# POSIXシェルについて

POSIXは、UNIX系OSのインターフェースに関する規格。  
POSIXに準拠するシェルのことをPOSIXシェルと呼ぶ。（`fish`は準拠していない）


## パフォーマンス

以下[shellbench](https://github.com/shellspec/shellbench)で`dash`・`bash`・ `zsh`のパフォーマンスを測定した結果。

```
# ./shellbench -s dash,bash,zsh sample/*
---------------------------------------------------------------
name                                 dash       bash        zsh
---------------------------------------------------------------
assign.sh: positional params    1,391,259    348,757    327,520
assign.sh: variable             1,697,477    504,335  1,164,166
assign.sh: local var            1,705,536    501,480  1,170,805
assign.sh: local var (typeset)      error    490,475  1,158,621
cmp.sh: [ ]                       833,262    275,396    197,401
cmp.sh: [[ ]]                       error    393,122    358,088
cmp.sh: case                    1,824,686    527,142    382,990
count.sh: posix                 1,225,109    382,351    810,241
count.sh: typeset -i                error    364,318    807,460
count.sh: increment                 error    429,496  1,099,849
eval.sh: direct assign          1,155,473    250,504    119,932
eval.sh: eval assign              695,700    132,989     97,642
eval.sh: command subs               4,618      2,686      2,608
func.sh: no func                1,781,726    477,697    415,864
func.sh: func                   1,451,109    254,464    116,069
null.sh: blank                      error      error  1,442,571
null.sh: assign variable        1,749,323    530,658  1,178,978
null.sh: define function        1,935,978    568,199  1,134,845
null.sh: undefined variable     1,814,041    421,084    392,327
null.sh: : command              1,833,552    480,573    416,079
output.sh: echo                 1,003,566    319,706    313,161
output.sh: printf                 944,468    322,299    313,943
output.sh: print                    error      error    317,124
subshell.sh: no subshell        1,789,673    476,324    411,253
subshell.sh: brace              1,789,560    466,399    330,783
subshell.sh: subshell               6,379      3,764      3,278
subshell.sh: command subs           5,843      3,157      3,268
subshell.sh: external command       1,940      1,581      1,437
---------------------------------------------------------------
* count: number of executions per second
```

基本的には`dash` > `zsh` > `bash`の順で速く、`dash`は`bash`のだいたい3倍から4倍速い。  
以上から、シェルスクリプトはPOSIX互換で書いて`dash`で実行するほうが、パフォーマンス的にもポータビリティ的にも良い。  
ただし、本当にパフォーマンスを重視するのであれば高級言語で書いてバイナリにしたほうが速く、メンテもしやすい。  
なお、インタラクティブシェルはパフォーマンスよりも使いやすさで選ぶべき。（個人的には、最初から入っていることが多く、必要十分な機能を持つ`bash`推し）

`bash`と`dash`の構文の違いは以下が詳しい。

- https://wiki.ubuntu.com/DashAsBinSh
- https://www.gnu.org/software/bash/manual/html_node/Major-Differences-From-The-Bourne-Shell.html
- https://mywiki.wooledge.org/Bashism

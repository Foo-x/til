# seqの初期化

基本的には以下の順で速い。

| 方法 | 代入していないインデックスの値 |
| --- | --- |
| newSeqUninitialized(N) | 不定 |
| newSeqOfCap(N) + setLen(N) | 不定 |
| newSeq(N) | 型の初期値 |
| newSeq() + setLen(N) | 型の初期値 |
| newSeqOfCap(N) + add | IndexOutOfBounds |
| newSeq() + add | IndexOutOfBounds |

- あらかじめ要素数がわかっており、アクセスする前にすべてセットできる場合

```nim
var arr = newSeqUninitialized[int](N)
for i in 0..<N:
  arr[i] = x
```

- あらかじめ要素数がわかっており、アクセスする前にすべてセットできるが、数値以外の型の場合
    - newSeqUninitializedは数値のseqでしか使えない

```nim
var arr = newSeqOfCap[string](N)
arr.setLen(N)
for i in 0..<N:
  arr[i] = x
```

- あらかじめ要素数はわかっているが、セット前のインデックスにアクセスする可能性がある場合

```nim
var
  arr = newSeq[int](N)
  # または
  # arr = newSeqWith[int](N, x)
```

- あらかじめ要素数の最大値はわかっているが、要素数はわかっていない場合

```nim
var
  arr = newSeqOfCap(Nmax)

arr.add(x)
```

- あらかじめ要素数の最大値がわからない場合
    - パフォーマンスが悪くてもメモリを節約したい場合は`newSeq() + add`
    - メモリを無駄に確保する可能性があってもパフォーマンスを良くしたい場合は`newSeqOfCap(N) + add`
        - このときのNは要素数を確実に超えるような値

`newSeq() + setLen(N)`の使いどころはない。(常に`newSeq(N)`で良い)

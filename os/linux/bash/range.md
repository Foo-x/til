# range

ブレース展開を使う方法

```sh
{0..5} # 0 1 2 3 4 5
{0..5..2} # 0 2 4
```

seqを使う方法

```sh
seq 0 3

# 0
# 1
# 2
# 3

seq 3

# 1
# 2
# 3

seq -s " " 5

# 1 2 3

seq 0 2 5

# 0
# 2
# 4
```

ブレース展開とは増分の場所が違う

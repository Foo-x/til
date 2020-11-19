# n行目以降を表示

`tail -n`に渡す値に+をつける。

```sh
echo -e "a\nb\nc" | tail -n +2

# b
# c
```

# DSVの各列を変数に格納しながら各行をループ

`read` で複数の変数名を指定すると、区切り文字で区切った各列が格納される。  

```sh
text='foo1,bar1
foo2,bar2'

echo "${text}" | while IFS=, read foo bar; do
    echo "${foo} - ${bar}"
done

# foo1 - bar1
# foo2 - bar2
```

区切り文字がスペースの場合は `IFS` の指定が不要。

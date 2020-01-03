# OR句のインデックス

(col1, col2)に複合インデックスが張られているtblに対して、下記SQL文を実行してもインデックスは使用されない。

```sql
select * from tbl where col1 = x or col2 = y
```

OR句でインデックスを使用したい場合はcol1とcol2にそれぞれ単一インデックスを張り、下記SQL文を実行する。

```sql
(select * from tbl where col1 = x)
union
(select * from tbl where col2 = y)
```

ただし、件数によってはOR句のままのほうが速いため、実際に実行して確認するのが無難。

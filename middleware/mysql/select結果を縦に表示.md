# select結果を縦に表示

select結果はデフォルトでは表で表示されるが、クエリの最後に`\G`をつけると縦に表示される。  

例

```
mysql> select Host,User from user;
+-----------+------------------+
| Host      | User             |
+-----------+------------------+
| %         | root             |
| localhost | mysql.infoschema |
| localhost | mysql.session    |
| localhost | mysql.sys        |
| localhost | root             |
+-----------+------------------+
5 rows in set (0.00 sec)

mysql> select Host,User from user \G;
*************************** 1. row ***************************
Host: %
User: root
*************************** 2. row ***************************
Host: localhost
User: mysql.infoschema
*************************** 3. row ***************************
Host: localhost
User: mysql.session
*************************** 4. row ***************************
Host: localhost
User: mysql.sys
*************************** 5. row ***************************
Host: localhost
User: root
5 rows in set (0.00 sec)
```

表だとカラム数が多いテーブルで表示が崩れるが、縦にすれば崩れない。

このオプションは`help`コマンドで確認可能。

> ```
> ego       (\G) Send command to mysql server, display result vertically.
> ```

# 起動したままMySQLのリストア

公式にある通り、下のコマンドを実行すれば良い。

`docker exec -i some-mysql sh -c 'exec mysql -uroot -p"$MYSQL_ROOT_PASSWORD"' < /some/path/on/your/host/all-databases.sql`

https://hub.docker.com/_/mysql

なお、sqlファイルが複数あって1度に実行したい場合はcatで結合してから渡せば良い。

`docker exec -i some-mysql sh -c 'exec mysql -uroot -p"$MYSQL_ROOT_PASSWORD"' < <(cat /some/path/on/your/host/*.sql)`

# Dockerで起動したMySQLにlocalhostで接続

Dockerで起動したMySQLに対して、WSLのシェルからは `mysql -u user -p -h localhost` で接続できない。  
MySQLクライアントはデフォルトでソケット接続を行うが、ソケットとして使う `mysqld.sock` はDockerコンテナの中にあり、WSLには無いため。  
`mysql -u user -p -h localhost --protocol=tcp` のようにしてTCP接続にすると接続できる。

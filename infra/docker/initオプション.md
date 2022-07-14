# initオプション

dockerではデフォルトでPIDが1でコマンドが実行されるが、シグナルハンドリングできなかったり、リソースリークしたりするケースがある。  
`docker run --init` や docker compose のinitオプションを使うと解決する。

[Dockerの--initフラグについて - Carpe Diem](https://christina04.hatenablog.com/entry/docker-init)

ちなみに停止も速くなる。

[docker run の --init をつけた場合（Docker 1.13 以降）](https://gist.github.com/mapk0y/3342ee187b11b0c05b168761761331bd)

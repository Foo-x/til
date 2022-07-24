# gitでリモートにつながらないとき

以下はSSH接続の場合のみ。

devcontainerではホスト側の SSH Agent にフォワードすることで、コンテナ内からgitのSSH認証を可能にしている。  
しかし、SSH Agent のソケットが `/tmp` に置かれるので、たまに削除されてしまってつながらなくなってしまう。  
`ssh-agent` を再実行して `SSH_AUTH_SOCK` を新しい値に修正してからdevcontainerを起動することで解決する。

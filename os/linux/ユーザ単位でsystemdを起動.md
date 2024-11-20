# ユーザ単位でsystemdを起動

1. ユーザの `~/.config/systemd/user/` ディレクトリに `<unit>.service` を置く
2. `systemctl --user daemon-reload`
3. `systemctl --user enable <unit>`
4. 作成したサービスが次のログイン時に自動で起動する
    - もちろん `systemctl --user start <unit>` ですぐ起動しても良い

ログイン後もサービスを起動したままにしたい場合は `loginctl enable-linger <username>` を実行する。

ユーザ単位のsystemdは `Install.WantedBy` に `multi-user.target` ではなく `default.target` を指定する。

`Failed to connect to bus` のエラーが出る場合は `export XDG_RUNTIME_DIR=/run/user/${UID}` をbashrcなどに設定して再ログインする。  
WSLの場合は `loginctl enable-linger <username>` を実行しないとエラーが出続ける。  
起動して2分後くらいに使えるようになる。

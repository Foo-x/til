# HTTPレスポンスヘッダによるキャッシュの無効化

秘密情報をキャッシュしてしまうと共用PCなどで漏洩してしまうリスクがある。

HTTPレスポンスヘッダに以下の設定を行うとブラウザによるキャッシュを防げる。

- Cache-Control: private, no-store, no-cache, must-revalidate
- Pragma: no-cache
- Expires: 0

なお、PragmaとExpiresは Cache-Control に対応していない環境向けの設定。

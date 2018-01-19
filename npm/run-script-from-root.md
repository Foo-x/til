# プロジェクトルートからのスクリプト実行

[パスを指定して実行](./in-different-path.md)を行うとき、スクリプトにパス指定があるとうまくいかない。
そのときはpackage.jsonがある場所からのパスを$PWDで指定できる。
例: `cmd ./foo/bar` -> `cmd $PWD/foo/bar`

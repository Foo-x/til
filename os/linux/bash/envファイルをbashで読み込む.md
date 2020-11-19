# envファイルをbashで読み込む

```
FOO=BAR

# hoge
XXX="YY Y"
```

のようなファイル（.envとする）の環境変数を読み込むには以下のようにする。

```bash
set -a
. .env
set +a

# 1行で
set -a; . .env; set +a

# コマンドのみに渡す
(set -a; . .env; set +a; foo)
```

# docker compose で一部を起動させない

デフォルトでは `services` に含まれるものはすべて `docker compose up` で起動する。一部を起動させたくない場合は `profiles` を設定すれば良い。

例

```yaml
services:
  foo:
    image: foo
  bar:
    image: bar
    profiles:
      - hoge
  baz:
    image: baz
    profiles:
      - hoge
```

このとき、`docker compose up` では `foo` だけが起動する。`docker compose --profile hoge up` または `COMPOSE_PROFILES=hoge docker compose up` とするとすべて起動する。  
なお、`docker compose up bar` のようにした場合は自動的に `hoge` が有効になる。すでに `foo` が起動している場合はすべてのサービス、何も起動していない場合は `bar` と `baz` のみが起動することになる。

プロファイルを複数指定したいときは、`docker compose --profile hoge --profile fuga up` もしくは `COMPOSE_PROFILES=hoge,fuga docker compose up` のようにする。

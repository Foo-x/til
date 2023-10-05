# 複数のComposeファイルを使用

`docker compose -f docker-compose.1.yml -f docker-compose.2.yml up` または `COMPOSE_FILE=docker-compose.1.yml:docker-compose.2.yml docker compose up` のようにすると複数のComposeファイルを使用できる。  
各ファイルに同じキーの設定が含まれている場合、後に指定したほうのファイルの値が使用される。  
なお、Composeファイルを指定しなかった場合、以下の挙動になる。

- `docker-compose.override.yml` が存在するとき
    - `docker-compose.yml` と `docker-compose.override.yml` を指定したときと同じ挙動
- `docker-compose.override.yml` が存在しないとき
    - `docker-compose.yml` を指定したときと同じ挙動


## ユースケース

### ローカル用の設定

リポジトリで管理している `docker-compose.yml` に対して、ローカルでのみ違う設定を使いたいとき。  
このときはローカルにのみ `docker-compose.override.yml` を置き、そちらにローカル用の設定を記載すると毎回Composeファイルを指定しなくて良いので便利。


### 環境ごとの設定

たとえば開発環境用の設定を `docker-compose.dev.yml`、本番環境用の設定を `docker-compose.prod.yml`、共通の設定を `docker-compose.common.yml` に記載する。  
起動時に `docker-compose.common.yml` に加えて環境用のComposeファイルを指定することで、設定を分けることができる。

なお、デフォルトの環境がある場合は、共通の設定を `docker-compose.yml`、デフォルトの環境用の設定を `docker-compose.override.yml` に記載すると毎回Composeファイルを指定しなくて良いので便利。  
デフォルトの環境以外で起動するときのみComposeファイルを指定することになる。


### 普段は使わない設定

Swagger UI によるAPI定義書を起動するサービス、DynamoDB Local の管理をする dynamodb-admin サービス、デバッグ用の設定など、普段は使わない設定を別のComposeファイルに記載し、必要なときにそちらも指定して起動する。  
なお、特定のサービス自体を普段使わない場合は、起動する際にサービスを指定すれば1つのComposeファイルでも管理できる。  
その際は、プロファイル機能を使うと便利。  
参考: [docker-composeで一部を起動させない](./docker-composeで一部を起動させない.md)

# Webアプリを安く運用する構成

個人開発などでWebアプリを安く運用する構成案（2020/11/06時点）

- フロントエンド
    - (GitHub Pages or Netlify) + CloudFlare
    - 静的にして無料でホスティング
    - CloudFlareを挟んで帯域を節約する
- バックエンド
    - (AWS Lambda + API Gateway) or VPS
    - 静的にできない処理はこちらで対応
    - Lambda + API Gateway (HTTP API)
        - 100万リクエストまで1.29USD、100万リクエストあたり0.2USD + 1.29USD
        - 実行時間1GB-秒あたり約0.000017USD
        - 読み込み1GBまで無料、1GBあたり0.114USD
- DB
    - DynamoDB or Firebase or VPS
    - DynamoDB（オンデマンド）
        - 書き込み1GBあたり約1.4USD
        - 読み込み4GBあたり0.285USD + 1GBあたり0.114USD（転送）
            - 転送は同一リージョン内であれば無料、また別リージョンでも1GBまで無料
        - ストレージ25GBまで無料、1GBあたり0.285USD
    - DynamoDB（プロビジョニング）
        - 書き込みキャパシティーユニット25個まで無料、1キャパシティーユニットあたり約0.00074USD
            - 1キャパシティーユニットで1秒あたり1KB実行可能
        - 読み込みキャパシティーユニット25個まで無料、1キャパシティーユニットあたり約0.00015USD
            - 1キャパシティーユニットで1秒あたり4KB実行可能
        - 読み込み1GBあたり0.114USD
            - 同一リージョン内であれば無料、また別リージョンでも1GBまで無料
        - ストレージ25GBまで無料、1GBあたり0.285USD
    - Firebase Cloud Firestore
        - 書き込み1日2万回まで無料、10万回あたり0.18USD
        - 読み込み1日5万回まで無料、10万回あたり0.06USD
        - 削除1日2万回まで無料、10万回あたり0.02USD
        - ストレージ1GiBまで無料、1GiBあたり0.18USD
- ストレージ
    - S3 or Wasabi
    - 画像、音声、動画などを置く
    - S3
        - ストレージ1GBあたり0.025USD
        - PUT/COPY/POST/LISTリクエスト1000回あたり0.0047USD
        - その他リクエスト1000回あたり0.00037USD
        - 読み込み1GBまで無料、1GBあたり0.114USD
    - Wasabi
        - ストレージ1GBあたり約0.79円
        - ただし最低利用料として1TB分かかる
            - 1TB未満しか保存していなくても1TBは請求される
    - ストレージは転送量が多くなりやすいのでS3は注意


## VPS比較

| サービス | メモリ | vCPU | SSD | 転送量上限 | 帯域 | その他 |
| --- | --- | --- | --- | --- | --- | --- |
| Lightsail 3.5USD | 512MB | 1 | 20GB | 1TB | ? | VPC内の転送は上限を超えても無料。ストレージは1GBあたり0.1USDで追加可能 |
| Lightsail 5USD | 1GB | 1 | 40GB | 2TB | ? | 同上 |
| Lightsail 10USD | 2GB | 1 | 60GB | 3TB | ? | 同上 |
| Lightsail 20USD | 4GB | 2 | 80GB | 4TB | ? | 同上 |
| Lightsail 40USD | 8GB | 2 | 160GB | 5TB | ? | 同上 |
| WebArena VPS Indigo 349円 | 1GB | 1 | 20GB | なし | 100Mbps | |
| WebArena VPS Indigo 699円 | 2GB | 2 | 40GB | なし | 100Mbps | |
| WebArena VPS Indigo 1272円 | 4GB | 4 | 80GB | なし | 500Mbps | |
| WebArena VPS Indigo 2798円 | 8GB | 6 | 160GB | なし | 1Gbps | |
| さくらのVPS 644円 | 512MB | 1 | 25GB | なし | 100Mbps | |
| さくらのVPS 880円 | 1GB | 2 | 50GB | なし | 100Mbps | |
| さくらのVPS 1738円 | 2GB | 3 | 100GB | なし | 100Mbps | |
| さくらのVPS 3520円 | 4GB | 4 | 200GB | なし | 100Mbps | |


## 転送量メモ

1リクエストあたり1MBとして、1万リクエストで10GB、100万リクエストで1TB。

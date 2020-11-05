# Webアプリを安く運用する構成

個人開発などでWebアプリを安く運用する構成案（2020/11/06時点）

- フロントエンド
    - GitHub Pages or Netlify
    - 静的にして無料でホスティング
- バックエンド
    - AWS Lambda or EC2 or Lightsail
    - 静的にできない処理はこちらで対応
    - Lambda
        - 100万リクエストまで無料、100万リクエストあたり0.2USD
        - 実行時間1GB-秒あたり約0.000017USD
- DB
    - DynamoDB or EC2 or Lightsail
    - DynamoDB（オンデマンド）
        - 書き込み1GBあたり約1.4USD
        - 読み込み4GBあたり0.285USD
        - ストレージ25GBまで無料、1GBあたり0.285USD
- ストレージ
    - S3 or Wasabi or EC2 or Lightsail
    - 画像、音声、動画などを置く
    - S3
        - ストレージ1GBあたり0.025USD
        - PUT/COPY/POST/LISTリクエスト1000回あたり0.0047USD
        - その他リクエスト1000回あたり0.00037USD
        - 読み込み1GBあたり0.114USD
    - Wasabi
        - ストレージ1GBあたり約0.79円
        - ただし最低利用料として1TB分かかる
            - 1TB未満しか保存していなくても1TBは請求される
    - ストレージは転送量が多くなりやすいのでWasabi以外は注意


## EC2 vs Lightsail

それぞれ最安のプラン

- EC2
    - 書き込み無料
    - 読み込み1GBあたり0.114USD
    - ストレージ1GBあたり0.12USD
    - インスタンス1時間あたり0.0054USD（720時間で約3.9USD）
- Lightsail
    - ストレージ20GB、読み込み1TBまで3.5USD

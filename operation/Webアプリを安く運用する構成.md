# Webアプリを安く運用する構成

## 無料枠

まずは無料枠で賄えないか検討する。

- [ずっと無料で使えるクラウドの「Free Tier」主要サービスまとめ。2021年版 － Publickey](https://www.publickey1.jp/blog/21/free_tier2021.html)
- [Cloudflare Pages・Vercel ・Netlify の違いや使い分けをまとめる](https://zenn.dev/catnose99/scraps/6780379210136f)
- [Fly App Pricing · Fly](https://fly.io/docs/about/pricing/)


## 有料

- バックエンド
    - (AWS Lambda + API Gateway) or VPS
    - Lambda + API Gateway (HTTP API)
        - 100万リクエストまで1.29USD、100万リクエストあたり0.2USD + 1.29USD
        - 実行時間1GB-秒あたり約0.000017USD
        - 読み込み1GBあたり0.114USD
- DB
    - DynamoDB or Firebase or VPS
    - DynamoDB（オンデマンド）
        - 書き込み1GBあたり約1.4USD
        - 読み込み4GBあたり0.285USD + 1GBあたり0.114USD（転送）
        - ストレージ1GBあたり0.285USD
    - DynamoDB（プロビジョニング）
        - 1書き込みキャパシティーユニット、1時間あたり約0.00074USD
            - 1キャパシティーユニットで1秒あたり1KB実行可能
        - 1読み込みキャパシティーユニット、1時間あたり約0.00015USD
            - 1キャパシティーユニットで1秒あたり4KB実行可能
        - 読み込み1GBあたり0.114USD
        - ストレージ1GBあたり0.285USD
        - 確保したユニットは使っていなくても課金される
            - ローンチしてすぐは予測が難しかったりアクセスがほとんど無かったりするのでオンデマンド、ある程度予測できるようになったらプロビジョニングに切り替えるのが良い
    - Firebase Cloud Firestore
        - 書き込み10万回あたり0.18USD
        - 読み込み10万回あたり0.06USD
        - 削除10万回あたり0.02USD
        - ストレージ1GiBあたり0.18USD
- オブジェクトストレージ
    - S3 or Wasabi
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
    - ストレージは転送量が多くなりやすいのでS3は注意


## 静的サイトホスティング比較

単位期間が記載されていない項目はすべて月あたり。

| サービス | ビルド数 | ビルド時間 | 成果物のサイズ | 転送量上限 | 商用利用の可否 |
| --- | --- | --- | --- | --- | --- |
| GitHub Pages | 10回/時 | - | 1GB | 100GB | 不可 |
| GitLab Pages | - | 400分 | 10GB | - | 可能 |
| Netlify Starter | - | 300分 | - | 100GB | 可能 |
| Netlify Pro $19 | - | 2500分 | - | 1TB | 可能 |
| Netlify Business $99 | - | 3500分 | - | 1.5TB | 可能 |
| Vercel Hobby | 100回/日 | 6000分/月、45分/回 | - | 100GB | 不可 |
| Vercel Pro $20 | 6000回/日 | 24000分/月、45分/回 | - | 1TB | 可能 |
| Cloudflare Pages Free | 500回/月 | 20分/回 | - | - | 可能 |
| Cloudflare Pages Pro $20 | 5000回/月 | 20分/回 | - | - | 可能 |
| Cloudflare Pages Business $200 | 20000回/月 | 20分/回 | - | - | 可能 |

サービスによってはファイル数やファイルごとのサイズにも制限があったりするので要確認。

ローカルでビルドしてpushしたものを使うようにすればビルド数やビルド時間を消費しないで済む。

上のリストに記載している制限を超える場合は Vercel Enterprise や AWS S3 などを使う。


## VPS比較

- [Lightsail](https://aws.amazon.com/jp/lightsail/)
- [WebArena VPS Indigo](https://web.arena.ne.jp/indigo/)
- [さくらのVPS](https://vps.sakura.ad.jp/)

| サービス | メモリ | vCPU | SSD | 転送量上限 | 帯域 | その他 |
| --- | --- | --- | --- | --- | --- | --- |
| Lightsail 3.5USD | 512MB | 1 | 20GB | 1TB | ? | VPC内の転送は上限を超えても無料。ストレージは1GBあたり0.1USDで追加可能。CPU使用率に制限あり |
| Lightsail 5USD | 1GB | 1 | 40GB | 2TB | ? | 同上 |
| Lightsail 10USD | 2GB | 1 | 60GB | 3TB | ? | 同上 |
| Lightsail 20USD | 4GB | 2 | 80GB | 4TB | ? | 同上 |
| Lightsail 40USD | 8GB | 2 | 160GB | 5TB | ? | 同上 |
| WebArena VPS Indigo 297円 | GB | 1 | 20GB | なし | 100Mbps | IPv6のみ |
| WebArena VPS Indigo 349円 | 1GB | 1 | 20GB | なし | 100Mbps | |
| WebArena VPS Indigo 699円 | 2GB | 2 | 40GB | なし | 100Mbps | |
| WebArena VPS Indigo 1272円 | 4GB | 4 | 80GB | なし | 500Mbps | |
| WebArena VPS Indigo 2798円 | 8GB | 6 | 160GB | なし | 1Gbps | |
| さくらのVPS 644円 | 512MB | 1 | 25GB | なし | 100Mbps | |
| さくらのVPS 880円 | 1GB | 2 | 50GB | なし | 100Mbps | |
| さくらのVPS 1738円 | 2GB | 3 | 100GB | なし | 100Mbps | |
| さくらのVPS 3520円 | 4GB | 4 | 200GB | なし | 100Mbps | |


## 従量制と定額制の比較

- 従量制
    - Pros
        - 使った分だけ支払えば良いので無駄がない
        - スケールしやすいことが多い
    - Cons
        - 適切な実装にしたり、モニタリングをしたりしないと想像以上の金額になることがある
        - 同じスペックだと定額制より高いことが多い
- 定額制
    - Pros
        - 実装ミスやSNSでの拡散などでリクエストが集中しても決まった料金以上はかからない
        - 料金の計画がやりやすい
        - 同じスペックだと従量制より安いことが多い
    - Cons
        - スペックを使いきれないと無駄になる
            - たとえば要求スペックが1コア4GBのときに、4コア4GBのプランしかないと3コア分の料金が無駄
        - プラン変更時に手動で移行することになり、スケールしにくいことが多い

小規模であれば従量制にすると数十円で済むことがあるのでお得な可能性が高い。ただし、サーバは使っていない間も料金がかかるので例外。こまめに止めるかサーバレスにする。  
中規模以上の場合は、負荷が読める箇所は定額制にして、読みにくい箇所は従量制にするとお得かつスケールしやすい。  
いずれにしても従量制で使う場合は料金アラートの設定と負荷対策が必須。定額制でもサービスを止めたくないのであれば負荷対策をしたほうが良い。


## 転送量メモ

1リクエストあたり1MBとして、1万リクエストで10GB、100万リクエストで1TB。

100Mbps は1ヶ月フルで使うとだいたい 32.5TB。


## その他

Oracle Cloud は無料枠が大きく、有料枠も安いが、いきなりBANされる上にサポートも適当なので使わないほうが良い。  

- [Oracle Cloud Infrastructureのアカウントが突然停止したので状況や調査内容を書いていく](https://zenn.dev/shinshin86/scraps/022e44712274fd?utm_source=pocket_mylist)
- [ORACLE Cloud Infrastructure どころか ORACLEさんから一方的にフラれたお話｜Dice.K｜note](https://note.com/dicek142/n/n22fa205324ed?utm_source=pocket_mylist)
- [Oracle Cloud Free Tier（Always Free） 理由なく突然使えなくなった話です。 - yumeno-miyukiのブログ](https://yumenohikari.hatenablog.com/entry/2022/04/09/235958)
- 上以外にも海外国内問わずBAN報告が大量にあり、いまだに理由がわかっていない

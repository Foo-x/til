# FunctionURLsをセキュアにする

Lambda Function URLs を使うと API Gateway なしでLambda関数にURLが付いて公開できる。  
しかし、そのままだとセキュリティまわりの保護が何もかかっていないので、DDoSなどを受けて料金が莫大になる可能性がある。  
対策として、以下の構成にする。

CloudFront + WAF -(OAC)-> Lambda Function URLs

L3/L4までの対策は自動で AWS Shield Standard が動く。  
L7の対策として、CloudFront + WAF を前段に置く。  
その際、OAC (Origin Access Control) で Lambda Function URLs を保護すると、直接Lambdaが実行されるのを防げる。

なお、全リクエスト共通のスロットリングを設定したいときは API Gateway で行う必要がある。

参考: [「CloudFrontがLambda Functions URLへのOACに対応！」の何がすごいか #lambda - Qiita](https://qiita.com/watany/items/4e3df4c6eef5ff01dc8f)

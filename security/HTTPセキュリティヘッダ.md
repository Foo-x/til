# HTTPセキュリティヘッダ

## キャッシュの無効化

秘密情報をキャッシュしてしまうと、共用PCなどで漏洩してしまうリスクがある。

以下のヘッダを設定すると、ブラウザによるキャッシュを防げる。

- Cache-Control: private, no-store, no-cache, must-revalidate
- Pragma: no-cache
- Expires: 0

Cache-Control の値はそれぞれ以下の設定。

- private: ローカルへのキャッシュのみ許可
- no-store: キャッシュしない
- no-cache: 毎回キャッシュをオリジンサーバで検証する
- must-revalidate: 有効期限切れのキャッシュをオリジンサーバで検証する

基本的には最も厳しい no-store だけで十分。他の値はブラウザやプロキシなどが no-store に対応していなかった場合のために設定する。対応されている中で最も厳しいものが優先される。

なお、PragmaとExpiresは Cache-Control に対応していない環境向けの設定。


## 自動でHTTPSに変換

HTTPでの通信は傍受されるリスクがある。これはHTTPでのアクセスをHTTPSにリダイレクトするだけでは回避できない。

以下のヘッダを設定すると、初回アクセス以降のHTTPリクエストが自動でHTTPSに変換される。この技術を HSTS (HTTP Strict Transport Security) ともいう。

- Strict-Transport-Security: max-age=31536000; includeSubDomains

max-ageの値は設定が有効な秒数。includeSubDomainsはサブドメインにも適用する設定。includeSubDomainsを使用する場合は、サブドメインも含めてすべてのサイトをHTTPSで運用する必要があるので注意。

preloadディレクティブを設定したうえで以下のサイトにドメインを登録すると、最初のアクセス時にも適用できる。

https://hstspreload.org/


## コンテンツ種別の推論を無効化

ブラウザによってはレスポンスのコンテンツ種別を推論して扱うことがある。これによって、Content-Type に text/plain を設定していても、HTMLとして扱われてJavaScriptが実行されるなどのリスクがある。

以下のヘッダを設定することで、コンテンツ種別の推論を無効化できる。

- X-Content-Type-Options: nosniff


## ダウンロードの明示

画面に表示する必要がないコンテンツを表示してしまうとJavaScriptが実行されるリスクがある。

以下のヘッダを設定することで、ダウンロード用のコンテンツであることを明示して、レンダリングされることを防げる。

- Content-Disposition: attachment; filename="example.json"

filenameは保存時のダイアログに設定されるデフォルトのファイル名であり、指定しなくても良い。


## リソースの読み込み元を制御

スクリプト・スタイルシート・画像などのリソースは同じオリジン、外部オリジン、インラインなどから読み込まれる。デフォルトでは任意のリソースが任意の場所から読み込めるため、XSSのリスクがある。

以下のヘッダを設定することで、リソースの読み込み元を制御できる。

- Content-Security-Policy: default-src 'self'

上の設定は同じオリジンのリソースのみを読み込むもの。  
細かい設定方法は以下のリンクを参照。

https://developer.mozilla.org/ja/docs/Web/HTTP/Headers/Content-Security-Policy


## リファラ情報の制御

ページ遷移時のリクエストヘッダに含まれるリファラ情報によって秘匿したいURLが漏れてしまうリスクがある。

以下のヘッダを設定することで、リファラ情報を制御できる。

- Referrer-Policy: same-origin, strict-origin-when-cross-origin

各値は以下の設定。

- same-origin
    - 同じオリジン: オリジン・パス・クエリを送信
    - 外部オリジン: リファラを送信しない
- strict-origin-when-cross-origin
    - 同じオリジン: オリジン・パス・クエリを送信
    - HTTPSからHTTPの外部オリジン: リファラを送信しない
    - それ以外: オリジンを送信

ブラウザが対応している値のうち、最も後ろにあるものが使用される。

# curlで全角文字を送信

リクエストに全角文字が含まれていて文字化けする場合は、ファイルから読み込むようにすれば解決する。

`curl -X POST -H "Content-type:application/json" https://example.com --data @request.json`

ファイルを作成したくない場合はハイフンで標準入力を代わりに使用できる。

`echo "foo" | curl -X POST -H "Content-type:application/json" https://example.com --data @-`

---

GETの場合は以下のようにする。

`curl -G --data-urlencode 'foo=テスト' example.com`

`-G` は POST data をクエリに変換しつつGETで送信するオプションで、`--data-urlencode` はパラメータをURLエンコードするオプション。

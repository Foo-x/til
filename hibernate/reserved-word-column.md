# カラム名が予約語の場合

そのままinsertなどをしようとすると、例外が発生する。
`hibernate.globally_quoted_identifiers=true`の設定を追加する。

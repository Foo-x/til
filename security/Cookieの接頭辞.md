# Cookieの接頭辞

- `__Secure-`
    - Secureフラグを設定してHTTPSである必要がある
- `__Host-`
    - Secureフラグを設定してHTTPSでありDomainを設定せずPathが `/` である必要がある
    - ドメインにロックされているという

以上の接頭辞について、制約を満たさない場合はブラウザが拒否するので、サブドメインの乗っ取りやHTTPでの中間者攻撃によるCookieの書き換えを防げる。

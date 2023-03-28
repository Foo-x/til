# `REPLACE INTO` と `INSERT ... ON DUPLICATE KEY UPDATE` の違い

`REPLACE INTO` は同じPKまたは同じUNIQUEな値を持つレコードを指定すると、元のレコードを削除してから `INSERT` する。  
指定したカラム以外はデフォルト値になり、`AUTO INCREMENT` が設定されている場合は新しく採番される。

`INSERT ... ON DUPLICATE KEY UPDATE` は同じPKまたは同じUNIQUEな値を持つレコードを指定すると、元のレコードを `UPDATE` する。  
指定したカラム以外は元のレコードの値のままになる。

以上からすべてのカラムを指定したときはほとんど同じ結果になる。

また、同じPKまたは同じUNIQUEな値を持つレコードが存在しないときはどちらも `INSERT` と同じ挙動になる。

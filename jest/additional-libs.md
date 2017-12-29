# 依存関係解決先の追加

importするモジュールのパスにデフォルトの`node_modules`以外も設定する。
package.jsonに以下のように設定。
```json
{
  "jest": {
    "moduleDirectories": [
      "node_modules",
      "libs"
    ]
  }
}
```

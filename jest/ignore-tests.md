# テストの実行スキップ

[依存関係解決先の追加](additional-libs.md)を`__tests__`内に作った場合などで、
デフォルトではそれらもテストを実行しようとしてしまうため、package.jsonに以下のように設定してスキップする。
```json
{
  "jest": {
    "testPathIgnorePatterns": [
      "/node_modules/",
      "/__tests__/__libs__/.*"
    ],
  }
}
```

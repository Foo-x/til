# snapshotテストのカバレッジが100%にならない場合

package.jsonの設定に以下を追加すると解決する可能性あり
```json
{
  "jest": {
    "browser": true,
    "mapCoverage": true
  }
}

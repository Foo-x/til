# NODE_PATHの設定

jest実行時の[rootからの相対パス指定](../nodejs/set-root.md)の設定ができる。
package.jsonに以下のように設定。
```json
{
  "jest": {
    "rootDir": ".",
    "modulePaths": [
      "<rootDir>"
    ]
  }
}
```

# NODE_PATHの設定

jest実行時の[ルートからの相対パス指定](../nodejs/ルートからの相対パス指定.md)の設定ができる。  
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

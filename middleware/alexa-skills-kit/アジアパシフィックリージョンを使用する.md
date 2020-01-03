# アジアパシフィックリージョンを使用する

- skill.json
```json
"apis": {
  "custom": {
    "endpoint": {
      "sourceDir": "lambda/custom"
    },
    "regions": {
      "FE": {
        "endpoint": {
          "sourceDir": "lambda/custom"
        }
      }
    }
  }
},
```
- .ask/config
```json
"apis": {
  "custom": {
    "endpoint": {
      "uri": "foo-uri"
    },
    "regions": {
      "FE": {
        "endpoint": {
          "uri": "foo-uri"
        }
      }
    }
  }
}
```

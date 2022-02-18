# async/awaitのエラー

async/awaitを使用しているjsで`regeneratorRuntime is not defined`のエラーが出る場合の対処。  
`babel-plugin-transform-runtime`をインストールし、以下の設定を追加する。
```js
module: {
  rules: [
    {
      options: {
        plugins: ['transform-runtime']
      }
    }
  ]
},
```

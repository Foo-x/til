# "Compared values have no visual difference"の対応

undefinedの値を持っているとtoEqualで表題のメッセージが出力される。  
JSONに変換すればOK
```js
expect(JSON.stringify(actual)).toBe(JSON.stringify(expected))
```

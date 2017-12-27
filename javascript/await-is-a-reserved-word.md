# "await is a reserved word"のエラー対策

以下はエラー

```js
() => {
  const bar = await baz()
}
```

以下のようにする

```js
async () => {
  const bar = await baz()
}
```

# async function内の例外

```js
test("foo", async () => {
  await expect(asyncFuncThrows()).rejects.toThrow()
})
```

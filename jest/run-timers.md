# タイマーを実行する

普通にテストを実行すると`setTimeout()`が実行されない。
実行するには以下のようにする。
```js
jest.useFakeTimers()

test("foo", () => {
  // 内部でsetTimeoutを使用している関数
  bar()

  // この時点ではsetTimeoutが実行されていない

  // ここで実行される
  jest.runAllTimers()

  // expect()
})
```

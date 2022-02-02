# スコープ外変数をmockで使用する

以下はエラー
```js
const baz = 1
jest.mock("foo", () => ({
  bar: jest.fn(() => baz)
}))
```

``The module factory of `jest.mock()` is not allowed to reference any out-of-scope variables``

スコープ外変数をmockにセットする場合は"mock"のprefixをつける。  
以下ならOK
```js
const mockBaz = 1
jest.mock("foo", () => ({
  bar: jest.fn(() => mockBaz)
}))
```

ただし、mockそのものを変数にすることは上記の方法でも不可能。  
以下はfooがundefinedになる。
```js
const mockFoo = {
  bar: jest.fn(() => 1)
}
jest.mock("foo", () => mockFoo)
```

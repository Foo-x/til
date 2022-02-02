# documentをモックにする

```js
const createElement = document.createElement
Object.defineProperty(document, "createElement", {
  value: jest.fn(),
  configurable: true
})

// test

Object.defineProperty(document, "createElement", {
  value: createElement
})
```

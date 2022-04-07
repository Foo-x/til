# range

```js
function* range(start, end, step=1) {
  for (let i = start; i < end; i += step) {
    yield i;
  }
}

// for (const i of range(10, 20)) { ... }

// Array.from(range(10, 20))

// [...range(10, 20)]
```

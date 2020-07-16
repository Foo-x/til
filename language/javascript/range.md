# range

```js
function* range(start, end, step=1) {
  let i = start;
  while (i < end) {
    yield i;
    i += step;
  }
}

// for (const i of range(10, 20)) { ... }

// Array.from(range(10, 20))

// [...range(10, 20)]
```

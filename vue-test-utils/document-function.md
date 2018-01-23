# document(window)の関数を使用する

`document.getElementById`など、document(window)の関数を使用する場合は以下のようにする。
(しなくてもgetElementできていたりするが、カバレッジに反映されないことがある)
```js
const foo = mount(component, {
  attachToDocument: true
})
```

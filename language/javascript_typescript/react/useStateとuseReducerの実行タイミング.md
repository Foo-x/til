# useStateとuseReducerの実行タイミング

useStateとuseReducerの実行は初期レンダリング時のみ行われる。

たとえば下のようにコンポーネントの引数を与えるとき、親から渡された引数が変わってもuseStateやuseReducerは再実行されない。

```tsx
const Component = ({value}) => {
  const [model, setModel] = useState(value)

  return <div>{value}</div>
}
```

つまり、useStateやuseReducerに与える値が動的に計算される場合はパフォーマンスを向上するために遅延したほうが良い。

```tsx
// incorrect
useState(expensiveFunc(arg))
useReducer(reducer, expensiveFunc(arg))

// correct
useState(() => expensiveFunc(arg))
useReducer(reducer, arg, expensiveFunc)
```

# Contextを状態と処理で分割

`useState` のstateとsetStateなど、1つのContextに状態と処理をどちらも入れてしまうと、処理だけを使うコンポーネントも値が変わったときに再描画されてしまう。  
状態と処理でContextを分けることで、処理だけを使うコンポーネントは再描画されなくなり、パフォーマンスが良くなる。

参考

- [Scaling Up with Reducer and Context – React](https://react.dev/learn/scaling-up-with-reducer-and-context)

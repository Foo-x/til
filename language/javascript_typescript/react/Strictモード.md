# Strictモード

Strictモードを有効にすると以下の挙動になり、バグを見つけやすくなる。

- レンダリングが複数回発生する
    - 純粋でない関数を見つけやすくなる
- useEffectが複数回実行される
    - クリーンアップ忘れを見つけやすくなる
- 非推奨APIを使用すると警告がコンソールに出力される

なお、開発モードでのみ動作し、本番ビルドには影響しない。

参考

- [\<StrictMode\> – React](https://react.dev/reference/react/StrictMode)

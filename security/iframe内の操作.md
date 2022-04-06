# iframe内の操作

iframe内の要素を埋め込んだ側から JavaScript で操作することはできない。  
ただし、以下の対応をすることで間接的に操作できるようになる。

- 埋め込まれる側の対応
    - 対応したい操作を実装する
    - `message` イベントのリスナーを登録し、受け取ったメッセージに応じて上で実装したものに振り分ける
    - レスポンスを返す必要がある場合は、`event.source.postMessage` で返す
- 埋め込む側の対応
    - 操作に対応するメッセージを `postMessage` でiframeに対して送る
    - レスポンスを受け取る必要がある場合は、`message` イベントのリスナーを登録して受け取る

詳細は下を参照。  
https://developer.mozilla.org/ja/docs/Web/API/Window/postMessage

実際は、埋め込む側の利便性のために、埋め込まれる側がラッパーAPIを用意することが多い。

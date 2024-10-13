# page_action の表示時に content_scripts をリロード

SPAのサイトではページ遷移時にリロードされず、デフォルトではリロード時にしか content_scripts は読み込まれないので、`matches` を満たさないURLから満たすURLに遷移しても content_scripts が読み込まれない。page_action を開いたタイミングに読み込めれば良い場合は、`permissions` に `activeTab` を追加した上で以下のようにする。

```js
// content_script.js

if (!chrome.runtime.onMessage.hasListeners()) {
  // ...
  chrome.runtime.onMessage.addListener((message: MsgToCS) => {
    // ...
  });
}
```
```js
// page_action.js
chrome.tabs.query({ active: true, currentWindow: true }, (tabs) => {
  chrome.tabs.executeScript(
    tabs[0].id!,
    {
      file: "content_script.js",
    }
  );
});
```

`content_script.js` で `if` 文の中に処理を入れないと、page_action を開くたびにリスナーが登録されてそれぞれ発火してしまう。

# 特定の条件でのみ page_action を表示

`permissions` に `declarativeContent` を追加した上で、`background.js` に以下のようなコードを追加する。（以下はURLのホストとパスで制限）

```js
chrome.runtime.onInstalled.addListener(function () {
  chrome.declarativeContent.onPageChanged.removeRules(undefined, function () {
    chrome.declarativeContent.onPageChanged.addRules([
      {
        conditions: [
          new chrome.declarativeContent.PageStateMatcher({
            pageUrl: { hostEquals: "foo", pathPrefix: "/bar" },
          }),
        ],
        actions: [new chrome.declarativeContent.ShowPageAction()],
      },
    ]);
  });
});
```

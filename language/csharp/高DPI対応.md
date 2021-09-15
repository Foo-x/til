# 高DPI対応

そのままではWindowsのディスプレイ設定から100%以上を設定されているときに座標がずれてしまう。  
プロジェクトを右クリックして「追加」→「新しい項目」→「全般」→「アプリケーションマニフェストファイル」を選択し、以下の行を `<assembly></assembly>` の中に追加する。

```xml
<application xmlns="urn:schemas-microsoft-com:asm.v3">
  <windowsSettings>
    <dpiAwareness xmlns="http://schemas.microsoft.com/SMI/2016/WindowsSettings">PerMonitor</dpiAwareness>
    <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
  </windowsSettings>
</application>
```

この状態で `Visual.PointFromScreen()` を使って座標を変換すればDPIが考慮される。

- 参考
    - https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI

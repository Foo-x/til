# DNSトンネリング

再現方法が不明だが、重いファイルをダウンロードしようとして長時間ネットワーク接続するとインターネットにつながらなくなることがある。  
WSL内で `ping google.com` がつながらず、`ping 8.8.8.8` だとつながる。  
Windows側だと `ping google.com` でもつながる。  
このとき、`wsl --shutdown` などで再起動しても解決せず、PCごと再起動する必要がある。

Windows側のホームフォルダの.wslconfig `/mnt/c/Users/<user>/.wslconfig` に以下の設定をするとWSL内からWindowsのDNS設定を使うようになり、再起動せずに解決する。

```
[wsl2]
dnsTunneling=true
```

なお、Windows 11 22H2 以上である必要がある。  
また、WSL 2.1 からはデフォルトで有効化されている。

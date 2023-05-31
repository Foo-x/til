# systemdを有効化

`/etc/wsl.conf` に以下を記載して再起動する。

```
[boot]
systemd=true
```

rsyslogやcronなどが自動で起動するようになる。

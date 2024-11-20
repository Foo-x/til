# systemdのログを確認する

`journalctl --unit <unit>` でsystemdのユニットのログを確認できる。  
`--unit` は `-u` でも可。  
ユーザインスタンスのログは `journalctl --user-unit <unit>`。  
`-f, --follow` で監視したり、`-n, --lines` で末尾から取得する行数を指定したりできる。

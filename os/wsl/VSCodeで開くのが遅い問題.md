# VSCodeで開くのが遅い問題

VSCodeで Remote - WSL を使って開くのが遅くなるときがある。  
settings.json に以下を設定すれば良い。

```
"remote.WSL2.connectionMethod": "localhost"
```

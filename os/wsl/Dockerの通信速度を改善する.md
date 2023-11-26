# Dockerの通信速度を改善する

WSLのdockerではbridgeネットワークだと通信速度が遅い問題がある。  
hostネットワークにすることで改善する。

devcontainerであればdevcontainer.jsonに以下の設定を行う。


```json
{
    "runArgs": [
        "--network=host"
    ]
}
```

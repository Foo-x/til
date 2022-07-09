# LiveShareの依存ライブラリ

LinuxやDockerでは、LiveShare の拡張機能をインストールするだけだと依存ライブラリが無くて使えないことが多い。  
以下のコマンドを実行する。

```sh
wget -O ~/vsls-reqs https://aka.ms/vsls-linux-prereq-script && chmod +x ~/vsls-reqs && ~/vsls-reqs
```

参考: [Linux のインストールの詳細 - Visual Studio Live Share - Live Share | Microsoft Docs](https://docs.microsoft.com/ja-jp/visualstudio/liveshare/reference/linux)

なお、Ubuntu 22.04 は上の手順でも解決しないので、代わりに下を実行する。

```sh
echo "deb http://security.ubuntu.com/ubuntu impish-security main" | sudo tee /etc/apt/sources.list.d/impish-security.list
sudo apt update
sudo apt install libssl1.1
```

根本的な解決策ではなくハックなので注意。

参考: https://github.com/MicrosoftDocs/live-share/issues/4646#issuecomment-1115120608

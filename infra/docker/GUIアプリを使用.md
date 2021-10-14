# GUIアプリを使用

1. ホスト側でXサーバを起動する
    - WindowsだとVcXsrvが有名
    - 個人的にはインストール不要かつわかりやすいMobaXtermを使用
2. コンテナ内で`export DISPLAY=<ホストのXサーバのDISPLAY>`を実行
    - MobaXtermの場合はタブを開いて最初に表示されるメッセージ内にDISPLAYが記載されている
3. コンテナ内で使用したいGUIアプリを起動

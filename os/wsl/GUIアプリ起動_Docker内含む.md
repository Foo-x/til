# GUIアプリ起動 Docker内含む

Windows 11 からはWSL2がデフォルトでGUIアプリに対応している。  
環境変数のDISPLAYも自動で設定されるので、.bashrc などで上書きすると逆効果な場合があるので注意。

Docker内のGUIアプリも、`docker run` の引数に `-v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY` を追加して起動すればOK。

# スタートアップでpowershell

スタートアップフォルダにps1ファイルを置くだけでは、テキストファイルが開くだけでスクリプトが実行されない。`powershell -ExecutionPolicy Bypass path\to\file.ps1` のように記入したcmdファイルを置くと実行される。

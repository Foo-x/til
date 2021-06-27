# WSLのシェルか判定

WSLのシェルは環境変数に`WSL_DISTRO_NAME`を持っているので、`[[ "${WSL_DISTRO_NAME}" ]]`でOK。  
検索すると`uname -a`や`/proc/version`や`/proc/sys/kernel/osrelease`に`microsoft`が含まれているかをチェックする方法が出てくるが、これはDocker内でもtrueになってしまうので使えない。  
なお、WSL1では`WSL_DISTRO_NAME`の代わりに`IS_WSL`が使える。

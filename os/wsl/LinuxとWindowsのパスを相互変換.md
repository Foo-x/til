# LinuxとWindowsのパスを相互変換

```
# WindowsのパスをLinuxのパスに変換
wslpath $path

# LinuxのパスをWindowsのパスに変換
wslpath -w $path

# LinuxのパスをWindowsのパスに変換（\ではなく/で区切る）
wslpath -m $path
```

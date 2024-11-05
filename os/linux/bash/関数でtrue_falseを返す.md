# 関数でtrue_falseを返す

関数からtrue/falseを返したいときはreturnの直前でtrue/falseコマンドを実行すれば良い。

```sh
is_win_dir() {
  case $(pwd -P) in
  /mnt/*)
    true
    return
    ;;
  *)
    false
    return
    ;;
  esac
}

if is_win_dir; then
  echo "is win dir"
fi
```

bashであれば `$(true)` と `$(false)` をreturnする方法もあるが、dashで動かない。

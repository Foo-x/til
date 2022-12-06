# throttleとdebounce

どちらも連続した同じ処理を間引くアルゴリズムだが、間引き方が違う。

- throttle
    - 一定時間ごとに処理を実行する
    - leadingがtrueのとき、最初の発火を実行する
    - trailingがtrueのとき、最初の発火を一定時間遅らせてから実行する
- debounce
    - 一定時間空いたら処理を実行する
    - leadingがtrueのとき、最初の発火を実行する
    - trailingがtrueのとき、最後の発火から一定時間空いたら実行する

たとえば以下のようになる。

```
# 1文字100ms、500msごとに間引くとする

# 生の発火データ
||| |   ||| |         | ||         ||| |||

# throttle (leading)
|       |             |            |    |

# throttle (trailing)
     |    |    |           |            |    |

# throttle (leading, trailing)
|    |    |    |      |    |       |    |    |

# debounce (leading)
|                     |            |

# debounce (trailing)
                 |            |               |

# debounce (leading, trailing)
|                |    |       |    |          |
```

以上から、定期的に実行したいときはthrottle、1回だけ実行させたいときはdebounceを使う。  
また、最初の発火をした瞬間に実行したいときはleading、最後の発火を実行したいときはtrailingを使う。

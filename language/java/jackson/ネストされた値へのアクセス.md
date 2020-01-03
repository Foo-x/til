# ネストされた値へのアクセス

ObjectNodeでネストされた値をget/setするときは以下のようにする。
```java
node.with("foo").get("bar");
node.with("foo").put("bar", "baz");
```

withではなくgetを使用すると、fooのキーが存在しない場合にエラー。

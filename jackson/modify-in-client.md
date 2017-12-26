# 使用する側で設定を変更する

アノテーションをクラス宣言に付与できない場合は以下のようにする。
```java
@JsonTypeInfo(use = Id.CLASS)
private static interface FooMixIn {}

ObjectMapper mapper = new ObjectMapper().addMixIn(Foo.class, FooMixIn.class);
```

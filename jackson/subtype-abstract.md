# abstractな値を解決させる

1. 型で判定(`@class`キーがシリアライズする際に付与される)
```java
@JsonTypeInfo(use = Id.CLASS)
public abstract class Foo {}
```

2. 名前で判定(`@type`キーがシリアライズする際に付与される)
```java
@JsonTypeInfo(use = Id.NAME)
@JsonSubTypes({
  @Type(name="child1", value=FooChild1.class),
  @Type(name="child2", value=FooChild2.class)
})
public abstract class Foo {}
```

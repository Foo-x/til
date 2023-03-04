# satisfiesの使いどころ

satisfiesは型をチェックするがwideningしない。  
型アノテーションや型アサーションはwideningする。

```ts
type A = {
  foo: string | number;
};

const a1: A = {
  foo: ''
};

const a2 = {
  foo: ''
} satisfies A;

// a1.foo は string | number なのでエラーになる
const b1: string = a1.foo;

// a2.foo は string なのでエラーにならない
const b2: string = a2.foo;
```

参考

- [TypeScript 4.9のas const satisfiesが便利。型チェックとwidening防止を同時に行う](https://zenn.dev/moneyforward/articles/typescript-as-const-satisfies)
- [Typescript 4.9 の satisfies Operator が気になる](https://zenn.dev/luvmini511/articles/55ad71c1ae99ba)

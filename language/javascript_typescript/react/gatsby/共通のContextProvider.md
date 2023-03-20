# 共通のContextProvider

Gatsby v5.6.0 から、全ページ共通で使いたいReactのContextがある場合、`gatsby-browser.tsx` および `gatsby-ssr.tsx` で `wrapRootElement` をexportすれば良い。

参考

- [Gatsby Browser APIs | Gatsby](https://www.gatsbyjs.com/docs/reference/config-files/gatsby-browser/#wrapRootElement)

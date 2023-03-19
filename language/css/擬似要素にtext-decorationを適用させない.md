# 擬似要素にtext-decorationを適用させない

要素に `text-decoration` を設定するとその擬似要素にも適用される。  
擬似要素に適用させないためには、`display: inline-block` を指定する。  
なお、`text-decoration: none` では変わらない。

# Vuetify
## Vuetifyとは
Vue.jsやNuxt.jsのUIフレームワーク。マテリアルデザインのコンポーネントを提供する。

## margin/paddinfの設定
Vuetifyのmargin/paddingは、以下のように設定する。
classに`m`または`p`を指定し、その後に`a`または`n`などを指定する。
```
<v-btn class="ma-2 pa-2">Button</v-btn>
```
### property
- `m`はmarginの略
- `p`はpaddingの略

### direction
- `a`はallの略: 上下左右全てに適用
- `t`はtopの略: 上に適用
- `b`はbottomの略: 下に適用
- `l`はleftの略: 左に適用
- `r`はrightの略: 右に適用
- `x`はx-axisの略: 左右に適用
- `y`はy-axisの略: 上下に適用
- `n`はnoneの略: 適用しない
- `0`は0の略: 0に適用

### size
設定している`2`は`1`で4pxの設定になる。よって、`2`は`8px`の設定になる。
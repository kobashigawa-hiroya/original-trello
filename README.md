

# クラス週案早見表（リポジトリ/プロジェクト/OSSなどの名前）
<img width="1667" alt="スクリーンショット 2021-03-09 18 13 22" src="https://user-images.githubusercontent.com/56257230/110448753-d054c200-8104-11eb-8c3f-917fa4bc1edd.png">


 
# DEMO
 
https://kobashigawa-hiroya.github.io/original-trello/
 
# 作成した経緯
- クラスの活動時、場所の確保・確認を円滑に行いたいと思い作成
- Vue.jsの基本を学ぶ


 
# 動作環境
 
 
* vue/cli 4.5.8
* vue@2.6.12
* Homebrew 2.16
* nodebrew 1.01
* node 12.8.0
 

 
# 使い方

## クラスを作成


<img src="https://user-images.githubusercontent.com/56257230/110449885-ff1f6800-8105-11eb-8ca6-c2b2c7ff1c41.gif" width="100%">

- クラスを追加をクリックし、クラス名を入力！　完了したら『追加する！』押すと追加される



<img src="https://user-images.githubusercontent.com/56257230/110451081-304c6800-8107-11eb-8675-feece7c8933d.gif" width="100%">
- Vue.Draggable使いドラック＆ドロップを実装
 
 
### v-modelを使ってデータバインディング
- :value = "title"で dataプロパティで定義したtitle をinputのvalueと紐付け

### gettersで合計を表示
```
getters: {
  totalCardCount(state) {
    let count = 0
    state.lists.map(content => count += content.cards.length)
    return count
  },
},
```
### Vue.Draggable使いドラック＆ドロップを実装
Vue.Draggableインストール
```
$ npm i -S vuedraggable
```
importで呼び出し
```
<template>
  <draggable>
  <!-- ★ここにドラッグ&ドロップさせたいコンポーネントを挿入します -->
  </draggable>
</template>

<script>
import draggable from 'vuedraggable'

```

 
# 学習した事

## 単一コンポーネント
- HTML ,JS, CSSを1つのファイルに配置しテンプレート化importで呼び出し繰り返し使える

## prpps 
- 親から子へデータ受け渡し

## $emit
- 子から親にデータ送る

## store 
- アプリケーションのデータの状態を保持するコンテナ
- state , mutation , actions , getters と4つの機能がある

### state
- アプリの全体のデータの状態を管理。現在のデータの状態確認とうに役立つ

### mutations 
- stateの更新を行う

### actions
- 非同期、API通信行う

### getters 
- Vueのcomputedと同様な動き、stateの値を算出したものを返す

- ディレクティブ（v-if, v-model, v-bind)を使いデータのバインディング、イベントの発火の仕組み
- vuexの概念を知る


## 苦労したところ

- props,$emitを使い親から子、子から親へのデータ受け渡しがうまく実装できず繰り返し調べたり実装を繰り返した

## 学んだ事
### コンポーネントのデータ受け渡し
<img width="295" alt="スクリーンショット 2021-01-30 7 19 03" src="https://user-images.githubusercontent.com/56257230/106333213-84c02480-62cb-11eb-81e0-befc412711da.png">

### storeを各コンポーネント
<img width="634" alt="スクリーンショット 2021-01-30 7 18 38" src="https://user-images.githubusercontent.com/56257230/106333394-ea141580-62cb-11eb-8416-d98afe6db727.png">
- コンポーネントが自立し管理されるのでデータにアクセスできる

# アンケート
- 全体の活動状況が可視化されているので、どのクラスがどこで活動をしているのか、またヘルプにスムーズに入れて良かった
- 活動時に他のクラスと使用場所が被ってしまう事を未然に防げた
- クラス人数を記載できたら尚いいかも
 

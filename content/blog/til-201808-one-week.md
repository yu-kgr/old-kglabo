+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-08-03"
description = "2018/08 - one week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/08 - one week I Learned"
type = "post"
draft = "true"
+++

# 今週、知った/学んだこと

<!-- tags = [""] -->

## 2018/07/30- Learned

7月30日（月）のToday I Leaned.

### JavaScript

#### ESLint

- 拡張子無しの.eslintrcはJSON,YAMLで記述可能ですが現在は非推奨です
- こんな感じのエラーを出してくれる
  - Unexpected block statement surrounding arrow body (arrow-body-style)
  - 関数がreturn分しか含まない場合は、ブレース（`{}`）とretun文とセミコロンを省略できる。

```JavaScript
() => {
  return 1;
}

// 省略したケース
() => 1
```

## 2018/07/31- Learned

7月31日（火）のToday I Leaned.

### JavaScript

#### ループ処理

- こういうのは古いらしい

```
# 古いコード
var iterable = [10, 20, 30];

for (var i = 0; i < iterable.length; i++) {
  var value = iterable[i];
  console.log(value);
}
```

- ループを回して、要素をひとつずつ取り出す・・・というコードは `for ... of`を使う。
  - イテレータプロトコル（反復処理プロトコル）というらしい。

```
# ナウいコード
const iterable = [10, 20, 30];

for (const value of iterable) {
  console.log(value);
}
```

#### Flow

- Facebook制の静的型チェッカー
- rootで`flow init`で利用可能
- 動作させたいファイルの先頭に `// @flow`とか`/* @flow */`とかいれると動作する 

#### Jest

- FacebookによるJavaScriptテストライブラリ / [Jest/快適なJavaScriptのテスト](https://jestjs.io/ja/) 
  - 他にもjasmine, mocha+chaiとか色々あったらしいが、これから触るマンとしてはよく知らん。
- 1パッケージいれるだけで「テストランナー/アサーション/モック/カバレッジ」の機能が利用可能
- [参考:ついに jest の軍門に降った](https://qiita.com/karak/items/9d0ebf7bc50085624913)
- `__tests__`ディレクトリ作ってその中にファイルを入れるか、 `.spec.js`または`.test.js`をつけると勝手にファイル見つけて実行してくれる。

### 今週の詰まった所

1. フロントエンド環境、どれが最新情報なのかわからない問題
  - 基本的に日本語で説明されている内容が古い事が多い
2. やたら書き方が変わる.babelrc
3. ぶっちゃけ覚えなくていいprototype（黙ってES2015のクラス宣言覚えとけばOK
4. jestを導入したらエラーが出る
  - 1に関係する内容だけど、モジュールが独自の進化を遂げてるケースがあるのでissueとか見に行く必要がある
5. 

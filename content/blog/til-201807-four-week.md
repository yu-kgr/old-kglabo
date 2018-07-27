+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-07-23"
description = "2018/07 - four week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/07 - four week I Learned"
type = "post"
draft = "true"
+++

# 今週、知った/学んだこと

<!-- tags = ["PullRequest", "React"] -->

## 2018/07/23 - Learned

7月23日（月）のToday I Leaned.

### GithubのPRについて

GithubのPRについてあんまり理解していなかったので、改めて備忘録。  
[参考:GitHubのReview機能が強化された](https://qiita.com/terra_yucco/items/fa08bd2a4b498963a313)

![githubのPRに対しての総評Review](/img/2018/07/github-pr-1.png)

- PR自体に `Review changes` より総評のような形でReviewを記載する事ができる
  - `Comment` / PRに対して承認などはせず、コメントのみを記載する際に利用。
  - `Approve` / PRに対して承認する事ができる。
  - `Request changes` / PRに対して修正依頼を出すことができる。（これを修正しないとマージする事ができない）
  - 感覚的には「Comment（見たよ）」「Approve（イイね）」「Request changes（ダメ）」

![PRの特定行のコードに対するコメント](/img/2018/07/github-pr-2.png)

- 特定行を指定し、コメントをいれる事も可能。（これは従来からある形らしい）

#### 備考

- とりあえず慣れるため、適当にCommentから入れていくことにしようかと思た。

#### 中カテゴリ

## 2018/07/26 - Learned

7月26日（木）のToday I Leaned.

### packge.json

- dependenciesは全てで利用するもの
- devDependenciesは開発はている時のみ利用するもの
  - Linterやビルド関係のパッケージなど / ちなみにdevに追加する場合は「yarn add --dev」で追加する


## 2018/07/27 - Learned

7月27日（金）のToday I Leaned.

### JavaScript

- [参考:イマドキのJavaScriptの書き方2018](https://qiita.com/shibukawa/items/19ab5c381bbb2e09d0d9)
  - もう覚えなくても良い書き方を解説されている為、学習計画上、無駄が減って非常にありがたい。
- 部分的に掻い摘んでメモしたい所のみ記載。

#### babel

- 現状は `preset-env` 使っておきゃいい

#### 変数

- こまけー事はいいから `const` 使っときゃいい

#### 関数宣言

- こまけー事はいいから `アロー関数` 使っとけばいい。
  - `function` は殺す

```
const hoge = () => {
  
};
```

#### 非同期処理

- こまけー事はいいから、 `async / await` 使っときやいい。
  - `then()`も殺す
- `async`つけたら、`await`ついてるやつが待ってくれるようになる。

#### 関数に引数セットを配列で渡す場合

- `apply()`は使わない
- スプレッド演算子 `...` 使う。


### 大カテゴリ

#### 中カテゴリ

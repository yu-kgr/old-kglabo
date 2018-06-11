+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-06-15"
description = "2018/06 - second week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/06 - second week I Learned"
type = "post"
draft = "true"
+++

# 今週、知った/学んだこと

<!-- tags = [ "git", ""] -->

## 2018/06/11 - Learned

6月11日（月）のToday I Leaned.

- ついに金沢も梅雨に入りました。そろそろ除湿機がほしい。
- そういえばRSSで購読してるTECHNICAL-CREATORブログさんで、今ちょうど読み勧めているフロントエンド・パンダ本について記事書かれてた。
  - [テクニカルクリエイター.com - はじめてのフロントエンド開発」を読みました。JSフレームワークに今触れるならコレ](https://technical-creator.com/first-frontend-dev/)

### gitについて

#### コミットした時のコメント内容を修正

- `git commit -m "typo comment"` した後は、 `git commit --amend -m "correct comment"` で修正できる`

#### 直近のコメントをまとめたい

- `git rebase -i HEAD~2` で、 最新2件のコミットをまとめる事ができる。
　
#### 指定したブランチを追従して、コミットを適用し直す

- `git rebase origin/master` でOK。


### PhantomJSとCasperJS

- ヘッドレスブラウザとそれを簡単に動かす為のものらしい。

#### PhantomJSとは

- JavaScriptを使用してスクリプトを作成できるヘッドレスWebブラウザ。マルチプラットフォームに対応している。
- GUIがないだけで、ブラウザでできる事は一通り行う事が可能『PhantomJS（CUIブラウザ）』
- 主にテストフレームワーク（Mochaとか）と組み合わせ利用される事が多い。
- [参考:PhantomJSとは](https://qiita.com/uest_kensington/items/82cd6978b4ac7afa6fdf)
- [参考:PhantomJS - Scriptable Headless Browser](http://phantomjs.org/)

#### CasperJSとは

- 上記のPhamtomJSを簡単に利用する事ができるようにするライブラリ
- Phantom（幽霊・亡霊）に対して1995年/アメリカ映画に出てくる少年ゴーストと同名な所が捻られてて面白い。
- 別のヘッドレスブラウザのSlimerJS（Firefox/Gecko）にも対応している。
- [参考:CasperJSでブラウザ操作を自動化しよう](https://qiita.com/a-kane/items/a5d4b8345bc9c5d2c15c)
- [参考:PhantomJS と CasperJS で複数ページを一括キャプチャする](https://www.tam-tam.co.jp/tipsnote/javascript/post8686.html)

### cheerio-httpcliについて

- Node.jsで静的サイトをスクレイピング/解析を行う事ができるモジュール。
- jQueryライクに操作可能 / UTF-8に自動変換 / ブラウザ指定でのUser-Agent切替可能。
- ただ、対応しているNode.jsのバージョンが古いのと動的解析はできないので注意
- [参考:Node.js用のスクレイピングモジュール「cheerio-httpcli」の紹介](https://qiita.com/ktty1220/items/e9e42247ede476d04ce2)
- [参考:cheerio-httpcli - Node.js用WEBスクレイピングモジュール](https://github.com/ktty1220/cheerio-httpcli)

---

## 2018/06/12 - Learned

6月12日（火）のToday I Leaned.

### カテゴリ2

#### 子カテゴリ2

---

## 2018/06/13 - Learned

6月13日（水）のToday I Leaned.

### カテゴリ3

#### 子カテゴリ3

---

## 2018/06/14 - Learned

6月14日（木）のToday I Leaned.

### カテゴリ4

#### 子カテゴリ4

---

## 2018/06/15 - Learned

6月15日（水）のToday I Leaned.

### カテゴリ5

#### 子カテゴリ5

---

### 雑感

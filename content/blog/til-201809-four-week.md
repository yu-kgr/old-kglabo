+++
author = "@yu-kgr"
categories = ["TIL"]
tags = ["Bitbucket", "git", "NoSQL"]
date = "2018-09-28"
description = "2018/09 - four week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/09 - four week I Learned"
type = "post"
draft = "false"
+++

# 今週、知った/学んだこと

## 2018/09/26- Learned

09月26日（水）のToday I Leaned.

### Bitbucket Server Extension

[Chrome WebStore](https://chrome.google.com/webstore/detail/bitbucket-server-extensio/hlagecmhpppmpfdifmigdglnhcpnohib)  : Bitbucket上でのプルリクエストー快適化してくれる。  
主な機能として「PR template」「レビュアーのグループ作成及び一括追加」「ブラウザによる通知設定」などが行える。  
PR Templateや、レビュアーの情報に関してはjsonで記載及び、jsonファイルのURLを記載する形でもOKな為、  
gistなどに記載すると便利。

## 2018/09/27- Learned

09月27日（木）のToday I Leaned.

git周りのコマンドは毎回忘れるので、何でもメモ📝

### git rebase

コミットした内容をまとめる事ができる。主に実装した機能ベースでコミットの粒度をまとめたい時になどに利用。  
3回コミットした後にPRを作成、マージしたいがコミットを1回分にまとめたい場合...

`git rebase HEAD~~~` を行ったら、rebaseの指示書が作成・表示される（表示順は↑が古く、↓が新しいコミット）ので、  
下記のコマンドを記載して行いたいアクションを指示する。

|コマンド|説明|
|---|---|
|(p)pick|コミットをそのまま残す|
|(r)reword|コミットメッセージを変更|
|(e)edit|コミット自体の内容を編集|
|(s)squash|直前のpickを指定したコミットに統合し、メッセージも統合|
|(f)fixup|直前のpickを指定したコミットに統合し、メッセージは破棄|

※ ちなみに、precommitなどで処理を行っている場合、その処理が走るので注意。

アクションを指示してコミットをrebaseした後はcommitIDが変わってしまう為、  
`git push -f`で強制的にpushを行う。

#### rebaseをミスった場合

`git rebase --abort` すればもとに戻る

### git stash（一次的な退避）

まだコミットしていないファイルを一時的に退避（stash）する事が可能  
作業途中でコミットできない状態だけど、ブランチを変更したい時などに利用。

|したい事|コマンド|備考|
|---|---|
|一時的に退避したい| `git stash save` |saveは省力可能|
|退避された変更の一覧を表示したい| `git stash list` | `<stash名>: WIP on <stashを行ったブランチ名>: <ハッシュ> <コミットコメント>` ※stashを行った時のHEADのもの / `list -p`とすると変更内容も見れる|
|退避された変更の一覧を表示したい| `git stash show <stash名>`| 各変更内容（ファイルなど）の一覧が見れる|
|一次退避した変更を復活したい|`git stash apply <stash名>`|指定した変更を復活しただけの場合は削除されていない|
|一次退避した変更を削除したい|`git stash drop <消したいstash名>`||
|一次退避した変更を復活&削除したい|`git stash pop <stash名>`||

変更範囲のの粒度が大きな場合はWIPコミットを行ってしまい、後ほどrebaseで整理するのも手かもしれない。

### git reflog（参照ログ）

`git reflog`とは、各個人のローカルリポジトリに存在しており、ブランチの切り替えやpull、履歴の書換、新規コミットなどを記録。  
`git reflog` で下記のようなHEADの移動履歴が表示される。

```text
59a9fd3 (HEAD -> master) HEAD@{0}: checkout: moving from tag-test to master
f70fa3b (origin/tag-test, tag-test) HEAD@{1}: reset: moving to HEAD
f70fa3b (origin/tag-test, tag-test) HEAD@{2}: commit: :wrench: add tag content
9ee7b4b HEAD@{3}: checkout: moving from master to tag-test
59a9fd3 (HEAD -> master) HEAD@{4}: commit: :memo: 2018-09#***作成
...
```

間違えて、`git reset --hard *****`等を行ってしまい、必要なコミットが消失してしまった場合、  
reflogを利用する事で該当のコミットにHEADを移動する事で救済する事ができる

1. `git reflog` or `git log -g`でreflogを確認
2. `git reset --hard HEAD@{3}`のような形でコミットのHEADに移動

## 2018/09/28- Learned

09月28日（金）のToday I Leaned.


### Couchbaseとは

NoSQLの一種でJSON形式でデータを登録できる「ドキュメント指向型」のデータベース

1. モバイル向けの機能が充実している
  - よく比較されるMongoDBと比べると、[モバイル向け機能](http://www.couchbase.com/nosql-databases/couchbase-mobile)・SDLが充実している為、それを利用する事で簡単にCouchbaseサーバとの通信を行う事が可能。
2. Enterprise機能が充実している
  - NoSQL自体が大量のデータを得意としている（RDBの場合はレコードの数が万になってくるとレスポンスが悪化してくる）

3. ドキュメント指向型ゆえの利便性

JSONでそのままデータ登録する事が用意な為、RDBで考える必要がある下記のような事が不要。

#### RDBの場合

1. テーブルを事前に定義
  a. 送信される可能性があるデータ項目を定義
  b. それぞれの項目の `Null/Not, Null, データ型`などを定義
  c. 送信データの仕様が変われば、テーブル構造も変更が必要（システム変更が必要）
2. 複数名データは個人ごとにバラす必要がある

#### ドキュメント指向型のNoSQLの場合

1. 事前に登録されるデータを定義しなくて良い
2. データ構造が変わっても問題なし
3. 配列データ / 複数名データであってもそのまま登録可

登録されるデータ型が変わる可能性が高いものに関しては採用する価値がありそう。

- これだけ見るとNoSQLのほうがいろいろとメリットが強い気がするがRDBのメリットとは一体…となってくる

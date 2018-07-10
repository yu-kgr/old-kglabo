+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-07-13"
description = "2018/07 - Second week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/07 - Second week I Learned"
type = "post"
draft = "false"
+++

# 今週、知った/学んだこと

<!-- tags = ["VSCode"] -->

## 2018/07/09 - Learned

7月9日（月）のToday I Leaned.

### VSCodeで独自のSyntaxHighlightを作る方法

- 結論 : テンプレートエンジン`ect`のSyntaxHighlightがSublimeText / Atomにはあるにも関わらず、VSCodeにはなかったので自作した。
  - [ect-highlight](https://github.com/yu-kgr/vscode-ect-syntax-highlight)
  - [参考:Visual Studio CodeでPlane Text(.txt)で自分独自記法のハイライト表示](https://prius.hateblo.jp/entry/2016/10/15/121707)
  - [参考:VS Code の ChangeLog 用 Extension を作成する](https://blog.kondoumh.com/entry/2018/01/12/084409)

1. ect.tmLanguageファイルを作成
  - [atom用の設定ファイルを参考](https://github.com/peppage/language-ect)に用意。
2. `The Yo Code Visual Studio Code Extension Generator`を使って、VS Code用にコンバートしつつ、生成されたファイルを微修正。
3. VS Codeの指定箇所に配置する

#### 所感

- HTMLで表示していたのでHTMLLinterがエラー検知してやっかいだったのがでなくなって満足！
- 尚、VS CodeのMarketへの公開方法はいまいちわからなかった。

## 2018/07/10 - Learned

7月10日（火）のToday I Leaned.

### Command Line

- [参考:progate コマンドライン学習コース](https://prog-8.com/lessons/commandline/study/1)
- （よくわかってなかったCommandだけ抜粋。）

#### pwd Command

- `Print Working Directory` の略。現在いるディレクトリがどこかを返してくれる

#### ls Command

- `list`の略。カレントディレクトリ内のディレクトリやファイルが一覧で表示される

#### mv Command

- `move` の略。ファイルの移動及び、同じディレクトリに違う名前で移動する事が可能。
- `mv  {移動させたいファイル名} {移動先のディレクトリ名}` または、 `mv  {移動させたいディレクトリ名} {移動先のディレクトリ名}` でデータを移動する事が出来る。
- `mv {リネームしたいファイル名}` `リネーム後のファイル名` で、データの名称を変更する事も可能。
- moveなのになんで名前変更できるねん。ってツッコミに対してはコチラの記事が参考になった。
  - [参考:mvでリネームができるわけをどこまで深く話せますか](https://qiita.com/junjis0203/items/9e8f642b04d9754f1139)

#### cp Command

- `copy` の略。ファイルのコピーを行う。
- `cp {コピーするファイル名} {コピーされる新しいファイル名}` でファイルをコピーする事ができる。
- 同様に`cp -r {コピーするディレクトリ名} {コピーされる新しいディレクトリ名}` でディレクトリ単位でコピーする事ができる。
  - ディレクトリは`-r`をつけないとコピーが実行されないので注意。
  - 尚、 `-r`は`--recursive`の略でコピー元にディレクトリを指定した場合、再帰的に（サブディレクトリも含めて）コピーするという意味らしい。

#### rm Command

- `remove` の略。ファイルの削除を行う。
- `rm {削除するファイル名}`でファイルを削除する事ができる。
- `rm -r {削除するディレクトリ名}` でディレクトリを削除する事ができる。
  - こちらもディレクトリは`-r`をつけないと削除が実行されないので注意。

  
----

## 2018/07/11 - Learned

7月11日（水）のToday I Leaned.

### 大カテゴリ

#### 中カテゴリ

---

## 2018/07/12 - Learned

7月12日（木）のToday I Leaned.

### 大カテゴリ

#### 中カテゴリ

---

## 2018/07/13 - Learned

7月13日（金）のToday I Leaned.

### 大カテゴリ

#### 中カテゴリ

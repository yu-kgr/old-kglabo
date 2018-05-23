+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-05-18"
description = "2018/05 - Second week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/05 - Second week I Learned"
type = "post"

+++
<!--tags = [ “git”, “submodule”, “CLI”, ”npx”, “名刺”, “回線速度” ]-->

## 今週、知った/学んだこと

### 2018/05/14 - Learned

#### Gitについて

- `git push origin HEAD` で、pushした場合は毎回、現在のCurrent branch　でpushする事ができる。
  - 毎回、`git push origin feature/HOGEHOGE/FUGAFUGA-1001` みたいなの入力してたのでかなり楽になって良い。
- gitconfigで指定されているuser.name等がgitに記録されるタイミングは `git commit`をしたタイミング。
  - 違うユーザアカウントでpushしてしまった為、gittconfigを書き換えて治そうとしたが、再度commitしないと治らなかった為、判明。
  - 個人のuser.nameで業務リポジトリにpushされてちょっと恥ずかしかった。

---

### 2018/05/15 - Learned

#### Gitについて

- ブログのテーマがsubmodule化されているが、毎回読み込みの仕方を忘れる
  - gitのsubmoduleは、メインのリポジトリで`git submodule update -i`とすると、submoduleの取り込みを行う。
  - git submodule foreach git pull origin master` で最新のsubmodule側のリポジトリの状態に更新してくれる
  - 尚、上記コマンドを入力する所は、メインのリポジトリのrootで大゛勝負な模様。

---

### 2018/05/16 - Learnded

#### 回線速度調査の手法

- CLIから回線速度のテストが出来るようにするfast-cliというものがあるらしい。
  - Nodeで動くので `npm install --global fast-cli`でインストールしたら、fastコマンドで動作するようになる。
  - [参考 : 回線速度のテストができる「fast」コマンドが便利だった - Qiita](https://qiita.com/suin/items/8398f0b07299a3cc194f)
- CLIでnpxを活用して自己紹介をする方法があった。
  - [名刺の代わりにCLIアプリを書く - Qiita](https://qiita.com/akameco/items/e0af9e3cdf1cdb6fca61)

---

### 2018/05/17 - Learnded

#### 知識メモ

- ハインリッヒの法則というものがある。
  - 内容としては、 1つの重大事故の背後には29の軽微な事故があり、その背景には300の異常が存在するというもの。
  - つまり、重大な事故がX件ある場合は、29倍の軽微な事故・災害があって、300倍のヒヤリ・ハットがあるという事。

#### セキュリティ対策

- セキュリティ対策は重要だという話。
  - ハッカーは脆弱性の隙間を突いて、最終的にサーバのrootをハッキングする為の行動を取る。
  - Ubuntu + Drupal構成のサーバがあった場合は、
    - 利用しているポートを確認。
    - Drupalのバージョン確認 → 脆弱性を確認してアタック
    - Drupalのアカウントを作成
    - Drupal上でPHPを実行可能にするPluginを導入
    - phpinfoでサーバ情報を取得 → サーバのバージョンを確認
    - サーバの脆弱性をアタックしてrootユーザのパスワードを取得

---

### 2018/05/18 - Learnded

#### ユーザテストについて
- ここ数日、某サービスのユーザテストの被験者として体験して思った事。
- サービス利用に至った背景や、テスト開始時点での状況説明を適切に行う必要がある。
- その説明を怠ると、そもそも把握している前提条件の元でテストを行っているつもりが、違う所で躓いてしまって求める問いと異なるテスト結果になりそうな為。

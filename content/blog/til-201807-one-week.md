+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-07-06"
description = "2018/07 - One week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/07 - One week I Learned"
type = "post"
draft = "true"
+++

# 今週、知った/学んだこと

<!-- tags = ["ssh", "PermissionError", "git", "marge", "rebase", "学習サービス", "docker"] -->

## 2018/07/02 - Learned

7月2日（月）のToday I Leaned.

### ssh接続時のPermissionErrorについて

- ssh keyのパーミッションがなんらかの理由で足りなくなる事があるらしいので、ちゃんと600設定してあげないといけない
- 複数のssh keyがある場合に発生する模様？
- [参考:MacのSSH接続でPermission denied (publickey)が出た時のおまじない](https://qiita.com/midasmn/items/5295f6799aa407f0fdcf)


## 2018/07/03 - Learned

7月3日（火）のToday I Leaned.

### gitのmargeとrebaseについて

- そういえば、branchを切ってからは基本的にPR飛ばしてからguthubやbitbucket側でmergeしてたから、margeとrebaseした事ない。
- hogeブランチとmasterブランチがある場合で考える。

####  margeの場合

- masterブランチにhogeブランチを差し出すスタイル。
- masterブランチのケツにhogeブランチコミットを乗せる。

#### rebaceの場合

- masterブランチの内容をhogeブランチに持ってくるスタイル。
- 名前の通り、hogeブランチ側の最初に最新のmasterブランチの内容をもってきて改変する

#### 備考

- チームの運用ルールにもよるが、rebaseは不要なコミットログをひとまとめにする際に利用されるケースが多そう。


### progateとcodeprepについて

- progateは実際に書かせる奴で、codeprepは穴埋めドリルやらせる奴。
- 個人的にはprogateで感覚掴んで、udemyで更になるほど感を高めた上でなんか作ってみるのが一番スムーズな気がする

## 2018/07/04 - Learned

7月4日（水）のToday I Leaned.

- stylishというGoogle拡張があり「webページのstyleを個人的に変更するだけ」なんだけど、何に使えるのやらとずっと思ってた所、ブラウザベースで利用するようなアプリケーションとかでサービスとしてはとても優秀だけど「ちょっと見づらい・使いにくい」をこっちで勝手に解決しちゃうという使い方が出来る事が判明。これは便利。
  - 便利。と思った瞬間、ユーザー情報を勝手に取得しているという記事が湧いててできたので代替アプリのstylusに変更した。

### docker

- 様々な用途に利用されるサーバの環境を簡単に用意できるやつ。
- 僕/みんなの考えた最強のサーバ環境みたいなテンプレ（dockerイメージ）を元にして、手元に同じ環境（dockerコンテナ）を簡単に用意する事が出来る。
  - ちなみに環境をDockerに閉じ込める事をDockerizeというらしい

#### ザックリしたdokcer / docker-conposeの違い

- `docker ***`はdockerコンテナ単体に対してなにかする処理
- `docker-compose ***`はdockerコンテナ複数に対してなにかしてくれる処理

- コンテナに対して個別でなにかしないといけない時は`docker ***` をする事がある
  - `docker logs ***` でコンテナのサーバログを追っかけたり
  - `docker exec -it **** /bin/bash` でコンテナのサーバーにログインしたり

- 構成された環境をまとめて立ち上げる処理等に関しては`docker-compose ***`を行う
  - `docker ***` コマンドで個別に立ち上げていく事も可能だが、それぞれのコンテナを起動する時に適切なオプションを指定してあげないととうまく連携しない。めんどくさい。
  - `docker-compose.yml`というファイルを用意して、起動時のオプションを記述しておく事でそれを起動時に参照していい感じに処理してくれる。

#### Dockerコンテナを作りかた

1. Dockerfileを元にDockerイメージを作成
  a. DockerHubからもってくる場合は、既に用意されているDockerイメージがあるのでDockerfileは不要
2. Dockerイメージを元にDockerコンテナを作成
3. 出来た！

#### Dockerコンテナの性質

`docker run --name sample1 -p 8090:80 -d nginx` のひと文でnginxサーバーが構築できちゃう。すごい。

1. 自分で名前をつけれる（`--name sample1`つけてる）
2. 名前の重複は不可（もう一個作る場合はsample1を消すか別名で）
3. コンテナはCreated（作成した状態）、Up（起動している状態）、Exit（終了した状態）などの状態を持つ
4. `docker run` は Created -> upまで一気にやっちゃう
5. コンテナは終了しないと削除できない
6. コンテナは閉じた世界
7. コンテナの世界から自分のPCに対して、必要に応じて穴をあける事が可能。

- `--name ****`はコンテナに名前をつける
- `-p 8090:80`はDockerコンテナ側では80番でnginxが起動しているのを、自PC側では8090番に紐づけして穴を開ける指定をしている

#### WebサーバとしてHTML表示してみる

- nginxで指定されているwebサーバのドキュメントルートとローカルのディレクトリのパスを関連付けると表示出来る。
  - `docker run --name sample1 -p 8090:80 -v $PWD/web:/usr/share/nginx/html -d nginx`
  - `-v $PWD/web:use/share/nginx/html` の箇所で `-v [自PC側のファイルパス]:[Docker側のファイルパス]`で穴を開ける（`$PWD` は現時点で自分がいるディレクトリらしい）

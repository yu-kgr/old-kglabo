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
draft = "false"
+++

# 今週、知った/学んだこと

<!-- tags = [ "git", "ヘッドレスブラウザ", "MultiAZ", "リージョン", "Availability Zone", "Amazon Elastic Container Registry", "Amazon Elastic Container Service", "DOMContentLoadedイベント", "Docker", "Key Management Service", "pbcopy", "jq", "tail", "kzrb"] -->


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

- 昨日出ていたPhantomJSのリポジトリがアーカイブされた模様。
  - [参考:JSer.info - PhantomJSの開発が終了しリポジトリがアーカイブ化された](https://jser.info/2018/06/11/phantomjs-ended/)
  - しかし、昨今はヘッドレスChromeやヘッドレスFirefoxを各社ブラウザベンダーが公式配布している模様。
    - [参考:ヘッドレスChrome ことはじめ](https://developers.google.com/web/updates/2017/04/headless-chrome?hl=ja)
    - [参考:ヘッドレスChromeの自動化ツール「Chromeless」を使って自動テストを実施する](https://dev.classmethod.jp/client-side/browser/chromeless/)


### AWSに関するもの

- Amazon Web Serviceゥゥゥ！

#### MultiAZとは一体

- なんかサーバの[冗長化](https://www.idcf.jp/words/redundant.html)だったり[ディザスタリカバリ](https://www.idcf.jp/words/dr.html)に関係するものの模様。
- [参考:リージョンとアベイラビリティーゾーン](https://docs.aws.amazon.com/ja_jp/AWSEC2/latest/UserGuide/using-regions-availability-zones.html)
- [参考:AWSのMultiAZについて調べたので残しておく](http://natural-hokke.hateblo.jp/entry/2014/10/24/133205)

##### リージョンついて

- 世界中の各地方に分散して用意された単一のデーターセンターが置いてある地域のこと（同じ国に複数ある事もある）
- {{地名}}リージョンみたいな呼び方する（東京リージョン / オレゴンリージョン）
  - 2018年2月頃、[大阪リージョンも出来た模様。](https://dev.classmethod.jp/cloud/release-osaka-local-region/)
- [参考:グローバルインフラストラクチャ](https://aws.amazon.com/jp/about-aws/global-infrastructure/)

##### Availability Zone（AZ）ついて

- 各リージョン（Tokyo/Oregon/Frankfurtなど）内で、物理的に離れた箇所にあるデータセンターのこと。
- Tokyoリージョン内にも複数のAvailabilityZoneが存在する。
- 各ユーザーが利用するリージョンが同じものになるとは限らない。
  - ユーザAは`ap-northeast-1a`が利用されたが、ユーザBは`ap-northeast-1b`を利用される…等。

```Markdown
# Tokyo リージョンの場合

- ap-northeast-1a
- ap-northeast-1b
- ap-northeast-1c
- ap-northeast-1d
```

##### Multi-AZについて

- サービスを１つのAZで構成したもの（EC2/RDS/ELB等）は`Single-AZ`と呼び、ービスを複数のAZで構成したものを`Multi-AZ`と呼ぶ。
  - AZ自体に障害があり、利用しているAZが死んだ場合にもサービスに影響を与えないようにする為に複数のAZで構築して障害耐性を上げる。
- 車の任意保険みたいなもの。AZが複数ある分、その分のコストはかかる。その代わりに…
  - EC2（Amazon Elastic Compute Cloud）       : 障害が起きてないAZが応答するのでダウンタイムが発生しない
  - RDS（Amazon Relational Database Service） : 勝手に切り替わる（自動フェイルオーバー）。1~6分程度かかる。インスタンスが2つなのでお金は2倍かかる
  - ELB（Amazon Elastic Load Balancing）      : CrossZone-LoadBalancingという設定を有効にしないとインスタンス数が違う場合、autoScaling時に負荷が偏るので注意。
- AZ単位の障害はメンテとか細かい不具合とか？ / リージョンでの障害はもはや大災害。
  - [AWS でいままで起きた大規模障害を振り返る](https://qiita.com/saitotak/items/07931343bcb703b101f8)


#### Amazon Elastic Container Registry

- 通称、Amazon ECR。Dockerのコンテナイメージを保存しておく為のレジストリ（設定情報のDB）。
- ECRに保存されているコンテナイメージは後述のECSなどのサービスにデプロイする事が可能。
- コンテナのイメージ操作はDockerCLIから行う事が可能で、イメージ自体はS3に保存されている。
- [参考:Amazon Elastic Container Registryとは](https://aws.amazon.com/jp/ecr/)

### Amazon Elastic Container Service

- コンテナ管理サービス。簡単にDockerコンテナを実行・停止・管理する事が可能。
- ざっくり言うと、クラスタ（複数のEC2インスタンスの上）で、FrontサーバとAPIサーバごとの役割に分けた個別のService（Dockerコンテナ）が動くかんじ。
- あとでちゃんと知ったほうが良さげな奴 : Cluster（クラスター）/ Task（タスク）/ Service（サービス）
- [参考:Amazon Elastic Container Service とは](https://docs.aws.amazon.com/ja_jp/AmazonECS/latest/developerguide/Welcome.html)
- [参考:Amazon EC2 Container Service(ECS)の概念整理](https://qiita.com/NewGyu/items/9597ed2eda763bd504d7)
- [参考:ECSの概念を理解しよう](http://www.mpon.me/entry/2017/11/19/200000)

---

## 2018/06/13 - Learned

6月13日（水）のToday I Leaned.

- 梅雨突入にもかかわらず奇跡的に天気予報が一週間連続で雨ではない金沢…！（奇跡か）
- ゼルダBoWやってて、トロッコ重ねて空中浮遊してたら、ハイラル城のてっぺんに到着してしまい、道中のザコ敵・中ボス全てすっ飛ばしてガノンと戦う羽目になる事案が発生。意図せぬエンドロールを見る羽目に。

### JavaScript

#### SEOについて

- GoogleはJSによるクライアントサイドのnoindex処理を非推奨としているので、表示したくないコンテンツがある場合はHTML自体に`noindex`をちゃんと入れよう。
- 現状、GooglebotはWebサイトを2回クロールしているが、1度目のクロールではJSレンダリングの解析はされず、2度目のクロールで解析されている。
- [参考:JavaScriptによるnoindex挿入をGoogleは推奨せず、JSレンダリングはセカンドウェーブのインデックス](https://www.suzukikenichi.com/blog/adding-noindex-tag-with-javascript-isnt-recommended/)

#### DOMContentLoadedイベント

- `window.onload` の場合は、`字句解析 -> 構文解析 -> DOM構築 -> 画像ファイル・サブフレームの読込み`完了後に実行するが、`DOMContentLoaded イベント`を利用した場合は、DOM構築したタイミングで処理を実行する。
- 結果としてDOM解析が完了した時点で実行しても良い処理の場合は処理速度の向上が見込めるので最適なイベントを選択しよう。

```JavaScript
// window.onload
window.onload = function() {
  return console.log('全ての画像とサブフレームのロードが完了後に処理');
};

// DOMContentLoaded
document.addEventListener("DOMContentLoaded", function(event) {
  return console.log('DOM構築が完了後に処理');
}
```

### Docker

- Dockerはアプリケーションを開発（developing）・移動（shipping）・実行（running）するための、コンテナ型の仮想環境プラットフォーム
- VirtualBoxみたいにホストOS上で仮想マシンを立ち上げてゲストOSを動かすのではなく、ホストマシンのカーネルを共有する事で、ホスト側仮想化ソフト -> ゲストOSの分のいろいろな手間がかからない。
- 環境をコード化して、共有することで複数人での同一な環境構築の手間が短縮できる・楽（雑）
- [参考:仮想環境についてまとめてみる](https://qiita.com/9en/items/f4eab2f61485a9f3885a)
- [参考:dockerで何ができるの？なんで使うの？を初心者がまとめる](https://qiita.com/hogehoge1234/items/b68e78cc4acb42cdca3d)
  - TODO:カーネルを個別に変えたい場合ってどんなケースなの？
- [参考:Docker-docs-ja](http://docs.docker.jp/engine/articles/dockerfile_best-practice.html)

### AWS

#### Key Management Service

- データキーをを使ってデータを暗号化できるが、データキーを紛失すると暗号化データが復号化されてしまうので、データキー自体を暗号化したマスターキーを用意。マスターキーはAWS側に保存できるよ。っていうサービス。
- リージョン毎にキーを管理する仕様。キーごとにアクセス範囲を設定可能。
- [参考:10分でわかるKey Management Serviceの仕組み #cmdevio](https://www.slideshare.net/torazuka/10key-management-service)
- TODO:暗号化するべきデータの基準とは一体…。

### Terminal

#### nodebrewのinstall-binaryについて

- 〈毎回忘れるのでメモ〉node.jsのバージョンマネージャーnodebrewについて。
- `nodebrew install <version>`にするとコンパイルありで、`nodebrew install-binary <version>` にするとコンパイルないことによってインストールする時間が高速になる（およそ1/15程度の時間差があるとの事）
- [参考:Nodebrewを使ってNode.jsを超高速にインストールする方法](https://qiita.com/yn-misaki/items/e92a47c662ea6d1236c1)
- ここまで調べて思った事「自分のPC環境は全て、anyenvで統一されているのでndenvでござった・・・:(」

#### pbcopyが非常に便利

- `cat <filName> | pbcopy` で指定したファイルの中身をコピペできる
- `cat ~/.ssh/id_rsa.pub | pbcopy` で公開鍵をコピーしたり、中身を共有したいファイルをコピペする時に便利。

## 2018/06/14 - Learned

6月14日（木）のToday I Leaned.

- 梅雨なのに金沢晴れてる！すげー！
- このTILのスタンスとしては個人的に「◯◯ってなんだっけ」って思った時に見返す備忘録用。
- また、性格診断による私のタイプは、[エンターテイナー型](https://www.16personalities.com/ja/esfp%E5%9E%8B%E3%81%AE%E6%80%A7%E6%A0%BC)らしい

### Shell Command

- 今日知った、気になったコマンドたち。

#### jqコマンド

- `brew install jq` で仲間入りしてくれる、JSONから簡単に値を抜き出したり、集計したり、整形して表示したりできるJSON用のgrepとかawkみたいなコマンド（らしい）
- [参考:jq コマンドを使う日常のご紹介](https://qiita.com/takeshinoda@github/items/2dec7a72930ec1f658af)
  - TODO:今度JSONファイルになんかする時に利用してみる

#### tail -F コマンド


- ファイルの末尾をCLI上で表示してくれるコマンドだけど、`-F`をつける事によって中身が更新されたりしても、そのまま続きを表示してくれる。
- error.logなどのファイルを見て問題解決を行いたい時に使うととても便利っぽい。
- [参考:tailコマンドのオプション「f」と「F」](https://qiita.com/sakito/items/7f65e16f10b3d754f307)

### TODO

追々ちゃんと理解したいもの。

- リバースプロキシについて | [参考:リバースプロキシ|「分かりそう」で「分からない」でも「分かった」気になれるIT用語辞典](http://wa3.i-3-i.info/word1755.html)
- KVS（Key-Value Store）について | [参考:KVS（Key-Value Store）とは](https://qiita.com/uenohara/items/23eb6ee1259f8a927445)
- Redisについて [参考:Redisの特徴と活用方法について](https://www.slideshare.net/yujiotani16/redis-76504393)
- Promiseとasync/awaiteについて | [参考:Promise と async/await を始めからていねいに](https://qiita.com/nabepon/items/1be1e83b0d17ee4f42a9)


## 2018/06/15 - Learned

6月15日（金）のToday I Leaned.

- Terminal/ShellCommandと表記ブレしてたが、そもそもこれはLinuxCommandという名称が正しいのではないか説

### Docker

- Dockerもっとわかりやすそうな資料あるやん！の巻
  - [参考:Dockerでよく使うコマンドまとめ](https://morizyun.github.io/docker/about-docker-command.html)
  - [参考:](https://qiita.com/aild_arch_bfmv/items/d47caf37b79e855af95f)

#### dockerとdocker-composeの違い

- dockerはコンテナの元になるイメージから、コンテナを作成する。
  - コンストラクタからインスタンス作成するイメージ

### React

- Reactが推奨するコンポーネントの種類
  - コンテナーコンポーネント
    - ロジック/処理を持つ事ができ、下記のプレゼンテーショナルコンポーネントを格納する。
  - プレゼンテーショナルコンポーネント
    - ロジックは持たず、状態毎のDOM（コンポーネント）をもつ。コンテナに格納される。

## 2018/06/16 - Learned

6月15日（土）のToday I Leaned.  
[kanazawa.rb meetup #70](https://kzrb.doorkeeper.jp/events/73677) に参加してきたので、ここ数日で出たTODOについて調べたりともくもくしてきました。

### TODOをひたすら調べる！

- 下記、調べた & 人に聞いた（ありがとうございやす）

#### Docker - カーネルを個別に変えたい場合ってどんなケースなのか？

- ケース: ホストOS自体を変えたい場合だったり、レジストリ自体を変えたい場合など
- 結　論: 自分のように手元で開発環境を作りたいという用途くらいであれば、基本的には気にしなくて良さそうな感じだった。

#### AWS Key Management Service（KVS）で暗号化するべきデータとは一体

- 各サービスを特定するような個人情報に該当するもの。
  - id・pass / 認証情報 / 秘密鍵など
- わかりやすく言うと「この◯◯はgithubに公開しちゃったら第三者に悪用されます」みたいなデータは該当（なるほど）

#### HTTPie

- CLIからいい感じにJSONとかを利用する事ができるらしい（？）
- [curlに変わる便利コマンドHTTPieを使ってみた](https://qiita.com/ytabuchi/items/02fa15ac209823a4d19f)

#### CIVIC HACKとAWSの話

- CIVICHACKとは、主にレガシーかつ封建的な環境に対してTechアプローチを入れることでいい感じに問題解決を図ろうぜって言うやつ。
  - うちの経営企画室に近い匂いを感じる。
- 今回のAWSのイベントでは、各企業のプロダクトの紹介がされているショーケースの横にAmazon IoT Enterprise Buttonがあって、その場で「FBのいいね」ができるようになっていた模様。

#### Ruby2.6.0について

- 現在はプレビュー版らしくおそらく年末あたりにリリース予定。
- 終端なしRange（endless range）という機能が便利そう。
  - `(1..10)`  endress range じゃない今までの終端ありのRange
  - `(1..)` # endress range
- 今までは冗長的な記述を行う必要があったが少ない記述量で実現したい事が実行できるようになるとの事。

### vue+vuex+nuxt

1. Local-Storageを使う際はなにかに注意しろ！（忘れた）
2. NuxtのデフォルトサーバーはCache-controlしないのでCDNと組みわせるとやばい。
  - Nuxtで組み上げるとどれ使いますか？って聞かれるので別のもの（Koaとか）を使うと良いらしい。

##### Promise - async/await

- ちょうどこれからPromise, async/awaitを学習はじめる所なので参考にしよう。
  - [参考:Promise と async/await を始めからていねいに](https://qiita.com/nabepon/items/1be1e83b0d17ee4f42a9)
  - [ES2017のasync/awaitのキソ練習](http://aligach.net/diary/20180526.html#p01)

#### 運用ブレスト聞きながら思ったこと

- 具体的な内容を記載するのは避けるけど…参考にしたい所が多い:-)
  - 仕組み・運用づくりがうまい
  - 質問の仕方だったり説明の仕方がうまい
  - 結論として落とし所を見つけるのかうまい
- （ただ個人的に、どこまでの人が権限を持って運営してるのあんまりわかっていない）
  - 後ほど聞いた所、5名くらいらしい（なるほど）

+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-09-07"
description = "2018/09 - one week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/09 - one week I Learned"
type = "post"
draft = "false"
+++

# 今週、知った/学んだこと

<!-- tags = ["IAM", "CloudTrail", "料金アラート", "料金の見積", "lightsail", "IAM", "IPアドレス", "EC2", "サブネット", ""CIDR"] -->

## 2018/09/03- Learned

9月3日（月）のToday I Leaned.

### サーバ監視ツール

両者、サーバの状態監視を行うが、
一言で言うと、JenkinsとCircleCiのような関係。

#### zabbix

- OSSの為無料で利用することができるがサーバの監視を行う為にzabbixを動かす為のサーバが必要になる
  - サーバ監視する為のサーバが監視されてねーじゃん問題でマトリョーシカ化する問題があるとかないとか
  - アプリケーションの状態監視も行う事ができる為、そこらへんは便利（らしい）
  - Jenkinsおじさんならぬ、zabbixおじさんが発生しがち

#### new relic

- サーバ監視を行うサービスとして展開している為、こちらのサーバにエージェントと呼ばれるものをインストールするだけで、new relic側のサーバに情報を送信してくれる
- 無料で利用する場合は1日分のレポートまでしか閲覧できない為、それ以上の事を行うたい場合は札束で殴りつける必要がある。
- 類似したサービスにMackerelやdatadogなどが存在する

論点としては、コストになりそう。

### AWS lightsailについて

- ボタンひとつ（+ちょっとしたlinuxコマンド知識）があればAWS上にVPSが$5/月から、すぐに用意できる
- サーバ構成などをスケールしたい場合にlightsailの場合はそれだけで完結している為、不便。
  - スナップショットを取って、別途用意したEC2に保存して移行する必要がある。

### AWS学ぶのによさげな奴

- [参考:AWS学習の0→1をサポートする講座「手を動かしながら2週間で学ぶ AWS 基本から応用まで」をUdemyでリリースしました](http://www.ketancho.net/entry/2018/09/03/074115)


## 2018/09/04- Learned

09月04日（火）のToday I Leaned.

「[手を動かしながら2週間で学ぶ AWS 基本から応用まで](https://www.udemy.com/aws-14days/)」というUdemy講座を受講開始した。

Day1 - AWSことはじめ

### IAMサービス

AWSのアカウントには rootユーザとIAMユーザが存在しており、用途毎にユーザーを使い分ける事がベストプラクティスとなっている。

#### ルートユーザ

- すべてのAWSサービスを使用できる
- 各種アカウントの設定、サポートプランの変更などを行う事ができる
- 通常の作業にルートユーザを用いてはならない

#### IAMユーザ

- 割り当てされたIAMポリシーで許可されたAWSサービスで利用できる
- 利用者ごとに払い出しを行い、通常の作業はこのIAMユーザーで行う。


### CloudTrail

- AWSに関する操作ログを保存するサービス。デフォルトで有効化されている
- 90日間分のログを確認する事が可能で、S3に証後を残していく
- 管理イベント（EC2インスタンスの作成やS3バケットの作成）、データイベント（S3バケット上のデータ操作やLambdaの実行）を保存可
  - 管理イベントのみ、最初から有効化されている


### 料金アラートについて

AWSの料金が$**を超えた場合、通知するように設定ができる。
これらはCloudWatch機能で設定する事が可能（他にも方法はありそう）

1. IAMで請求の設定を行う
2. 請求のアラートを受け取る設定にするCloudWatchで料金アラートを行う
3. CloudWatchで料金アラートを設定する

### AWS料金の見積もり方

1. 「<AWS サービス名> pricing」で検索する
2. [Simple Monthly Calculator](https://calculator.s3.amazonaws.com/index.html) を利用する

## 2018/09/05- Learned

09月05日（水）のToday I Leaned.

「[手を動かしながら2週間で学ぶ AWS 基本から応用まで](https://www.udemy.com/aws-14days/)」というUdemy講座を受講開始した。

Day2 - EC2を使ってサーバ立てる

### EC2について

- 仮想のコンピューティング環境
  - いわゆるサーバを利用するサービス
  - OSより上のレイヤについては自由に設定可能
  - [従量課金制](https://aws.amazon.com/jp/ec2/pricing/on-demand/)
- EC2を使う上での5大ポイント
  1. OS/Imageの選択が可能
    - RedhatやLinuxなど選べる
  2. インスタンスタイプを選択できる
    - 一般的な構成、コンピューティング特化、メモリ最適化、GPU最適化などニーズに合わせたものを選択できる
  3. ストレージり選択が出来る
    - HDD/SDDの選択が可能
  4. セキュリティグループの設定
    - どこからの通信ならEC2に接続可能なのかについて設定する
  5. SSHキーペアの設定
    - 公開鍵/秘密鍵の設定を行う

### EC2インスタンスの起動の仕方

基本的に[こちら](https://ap-northeast-1.console.aws.amazon.com/ec2/v2/home?region=ap-northeast-1#LaunchInstanceWizard:)のウィザードに従って作成していく。一連の流れは下記の通り。

1. AMI の選択
  - AWS Market Placeは各社が作成したAMI。
2. インスタンスタイプの選択
3. インスタンスの設定
4. ストレージの追加
5. タグの追加
6. セキュリティグループの設定
  - インスタンス作成時のセキュリティグループの作成はSSHの場合は自分が普段接続するグローバルIPを設定してあげるなどしたほうが良い。

### EC2インスタンスに接続して、ミドルウェアの導入

1. `ssh -i ***.pem ec2-user@{IPv4 パブリック IP}` で接続する
2. 真っ白な状態なので `sudo yum install httpd` など行ってサーバに必要なミドルウェア群を導入していく

### AMI（Amazon Machine Image）を取得する

#### AMIとは

- EC2にある断面を保存して、それをEC2インスタンスとして利用できるようにするもの

#### Snapshotとは

- ディスク（EBS）の断面をとって、それをEBSを作るものになる
- データ用のEBSだけバックアップが取りたいという場合はSnapshotになる。
  - ボリュームタイプがルートのSnapshotをとった場合はAMIに利用する事もできる。

AMIもSnapshotも静止点をとって取得する事 / 稼働中に取得するとデータの不整合をおこす為。
  - 静止点 = インスタンスの停止

1. インスタンスを停止する（アクション ->インスタンスの状態 -> 停止）
2. AMIイメージの作成（アクション -> イメージ -> イメージの作成）
3. AMIの画面から「インスタンスの作成」を選択するか、ウィザードで「マイ AMI」を選択して、作成したAMIを選択
4. あとは前回同様にウィザードを進めればOK

### EIP（Elastic IP Address）を利用してIPアドレスを固定する

インスタンスを停止すると、再起動するたび異なるIPが付与されてしまい、  
毎回接続先が変わってしまう為、EIPを利用してIPを固定する必要がある。

1. 左メニューから Elastic IPからポチポチするだけで余っているIPが払い出される

#### 注意

EIPは実行中のインスタンスに関連付けられている場合は無料だが、下記の場合は料金がかかる為注意。

1. 実行中のインスタンスに対して、追加でEIPを関連付けている
2. 実行中のインスタンスと、関連付けられていないEIP

## 2018/09/06- Learned

09月06日（木）のToday I Leaned.

「[手を動かしながら2週間で学ぶ AWS 基本から応用まで](https://www.udemy.com/aws-14days/)」  
Day3 - VPCを使ってネットワークを構築する

### AWSにおけるネットワーク

下記座学にて説明

- リージョン / アベイラビリティゾーン
- VPC / サブネット

実際に手を動かして以下の内容を学ぶ

- VPCを作る
- パブリックサブネットを作る
  - Webサーバを構築する
- プライベートサブネットを作る
  - DBサーバを構築する

![img](/img/2018/09/2018-09-11-08-31-03.png)

### リージョンとは

- 東京にあったり、オレゴンにあったりする `複数のデータセンター` をたばねたもの。

### アベイラビリティゾーンとは

- リージョンの中にある複数の `データセンター` の事。

### VPCとは

- それぞれのアカウント毎に独立したネットワークを作成する事ができるサービス
- AZをまたがって作る形となり、アカウント内で複数作る事ができる。

### サブネットとは

- VPCの中の一部のネットワーク帯域をIPアドレスを指定して作るサービス
  - このサブネットはグローバルに利用するものだよ/このサブネットはDB用に利用するのでグローバルに晒したくないよみたいな事を指定できる
  - AZごとにサブネットを作ったほうが、障害時にひとつのサブネットが死んでもサービスを止めないようにできる為、AWSはマルチサブネットを推奨している。

### IPアドレスとは

>IPアドレスは、コンピュータ内部では2進数で処理されることから、32ビットの整数値で表されます。

`11000000 10101000 00000010 00000001` = `32bit（2進数）`

>しかし、人には2進数はわかりにくいため、分かりやすくするために32ビットの整数値を8ビットずつ4つに分割して10進数でIPアドレスを表します。

`11000000.10101000.00000010.00000001`
　　　↓
`192.168.2.1` = `8bit * 4（10進数）`

つまり、IPアドレスは `10.20.30.40/32`のような形で記載され、  
8bitの数字が．で区切られた形で記載される。

ちなみに `192.168.2.1` には末尾に`/32`が省力されている為、  
`192.168.2.1/32` という表記が正式らしい

### CIDRとは

- Classless Inter-Domain Routingの略で、クラスの概念を使わないIPアドレスの割当・経路情報の集成を行う技術の事らしく、IPアドレスの管理方法。
- [参考:CIDR](https://wa3.i-3-i.info/word11989.html) / IPアドレスのレンジを示すもの。
- アドレスに続いて、`/`とネットワークアドレスのビット数を表記する形で、IPを振り当てる事ができるホストの数が変わる。

```text
# 例
IP Address : 192.168.10.1
Subnet Mask : 255.255.255.0
```
の場合は、`192.168.10.0/24` と表記される。


先程の `192.168.2.1/32` が `192.168.0.0/16`になった場合、  
末尾の`8bit*2`の箇所、 `.0.0`が`*`的な扱いになる。

- つまり `192.168.0.0/16` == `192.168.0.0 〜 192.168.255.255` という感じ

同様に下記のような形になる。

```text
- 123.456.789.101/32 : 一つのIPアドレス
- 123.456.***.***/28 : 14のIPアドレス帯
- 123.456.789.***/24 : 254のIPアドレス帯
※AWSの場合は5つ分のアドレスが予約されているので上記より更にマイナスされる
```

## 2018/09/07- Learned

09月07日（金）のToday I Leaned.

### AWS IAMサービスについて

- [AWSを安全に使うために（IAMのベストプラクティス）](http://bit.ly/2NmwMMG)の内容が非常にわかりやすかった。

#### パスワードポリシーは適切に決める事

ポリシーのルールに迷う場合はPCIDSSの要件を満たすルールを参照すると良さそう

```
1. パスワードの最小長：8文字
2 少なくとも 1 つの大文字が必要
3. 少なくとも 1 つの小文字が必要
4. 少なくとも 1 つの数字が必要
5. パスワードの有効期間（日数）：90日
```

### APIまわりのあれこれ

- TODO: 後ほど詳細を調べて記事にまとめる事にする。

#### 登場人物

- Rest
- RESTful
- GraphQL

#### 参考文献

- [5分で絶対に分かるAPI設計の考え方とポイント (1/6)](http://www.atmarkit.co.jp/ait/articles/1511/19/news022.html)
- [RESTful APIとは何なのか](https://qiita.com/NagaokaKenichi/items/0647c30ef596cedf4bf2)
- [RESTful APIのURI設計(エンドポイント設計)](https://qiita.com/NagaokaKenichi/items/6298eb8960570c7ad2e9)

<blockquote class="twitter-tweet" data-lang="ja"><p lang="en" dir="ltr">GraphQL and Rest Differences explained with burgers 🍔 <a href="https://t.co/uNm3sJ8JY4">pic.twitter.com/uNm3sJ8JY4</a></p>&mdash; Sara Vieira @ 🇵🇱 (@NikkitaFTW) <a href="https://twitter.com/NikkitaFTW/status/1011928066816462848?ref_src=twsrc%5Etfw">2018年6月27日</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" data-conversation="none" data-lang="ja"><p lang="en" dir="ltr">I do a similar REST vs. GraphQL comparison with pizza. With REST, you can only choose from three kinds of pizza (resources). If you want something custom, you have to manually combine the toppings from the available pizzas.<br><br>With GraphQL, you can order any custom pizza you want! <a href="https://t.co/dcbVFpmjSu">pic.twitter.com/dcbVFpmjSu</a></p>&mdash; Peggy Rayzis 👩🏼‍💻 (@peggyrayzis) <a href="https://twitter.com/peggyrayzis/status/1011981410465468416?ref_src=twsrc%5Etfw">2018年6月27日</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


## 今週の感想

- AWS学習を通じる事でWebアプリケーション作成時の全体像みたいなものかせ少しずつ見えた着たような気がするので、引き続き少しずつ学んで行きたい所存。
- IPアドレス/サブネットマスク/CIDRあたりはちょっとわかったようなわからんような…って感じなのでもうちょい調べたい。

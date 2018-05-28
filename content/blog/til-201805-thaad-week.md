+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-05-25"
description = "2018/05 - Thaad week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/05 - Thaad week I Learned"
type = "post"
draft = "false"
+++
# 今週、知った/学んだこと

<!-- tags = [ "slackbot", "MD5", "SHA256", "Atomic Design", "Linuxコマンド","Storybook", "npx", "webpack" "require"] -->

## 2018/05/21 - Learned

5月21日（月）のToday I Leaned

### SlackBotについて

SlackBotを作る際に利用するSlack API Tokenには種類がある。

- Slackのほぼすべての機能を使えるレガシートークン
  - [Slack APIのTokenの取得・場所](https://qiita.com/ykhirao/items/0d6b9f4a0cc626884dbb)
  - 流出した場合は、チャンネルの削除から何からやり放題。必要な機能にしかアクセス権を与えないトークン
  - [Slack API 推奨Tokenについて - Qiita](https://qiita.com/ykhirao/items/3b19ee6a1458cfb4ba21)
  - 流出しても必要最低限の権限しか与えられていない。

### 暗号化について

- MD5よりSHA256のほうが安全らしい
  - [md5とsha256を使ってみた - Qiita](https://qiita.com/t-mochizuki/items/5ab21b6ae9b1941122ab)

## 2018/05/22 - Learned

5月22日（火）のToday I Leaned

### Atomic Designについて

- パーツ・コンポーネント単位で定義していく UI デザイン手法。
- アプローチ / 考え方
  - エディトリアル / グラフィックからではなく、マークアップ / コーディングからUI設計を行っていく手法で、メリットとしてUIが一定の品質でテンプレ化される事によって、非デザイナーでも一定水準の品質のプロダクトデザインを担保する事が可能。
  - 参考 : [Atomic Design を 分かったつもりになる](http://design.dena.com/design/atomic-design-%E3%82%92%E5%88%86%E3%81%8B%E3%81%A3%E3%81%9F%E3%81%A4%E3%82%82%E3%82%8A%E3%81%AB%E3%81%AA%E3%82%8B/)

```
# 構成要素
- atoms / 原子（あとむす）
  - UI部品の最小単位
- molecules / 分子（もれきゅーる）
  - 機能的なまとまり
- organisms / 生体（おーがにずむす）
  - ページ内のセクション
- templates / テンプレート（てんぷれーと）
  - ワイヤーフレームとなるもの
- pages / ページ
  - テンプレートに内容を入れた、実際表示される状態
```

- 考え方としてはBootstrapに近い。

## 2018/05/23 - Learned

5月23日（水）のToday I Leaned

### Next.jsについて

- とても楽に React の web application を開発する事が可能。
  - ReactをSSR（Server Side Rendering）し、Babelで書くことが出来、buildもしてくれつつ、Universal JavaScript Web Applicationを作成する事ができるOSSのWeb Framework。
  - Reactの学習をした後、Next.jsを使えばShadow DOMの修学は問題ない
  - 仕様が明確で拡張性も高い。

## 2018/05/24 - Learned

5月24日（木）のToday I Leaned

- 金沢の最高気温は19/7度、最低気温は16.7度。
- 体調不良にてしんでおりました。

## 2018/05/25 - Learned

5月25日（金）のToday I Leaned

- 1.5hほどもくもくする時間を確保。

### Linuxコマンドについて

#### mkdir

- `mkdir hoge fuga` で 複数ディレクトリを同時作成する事が可能
- `mkdir -p hoge/fuga piyo/foo` で多階層ディレクトリを作成する事が可能

#### touch

- `touch` コマンド自体は指定したファイルのタイムスタンプを変更するコマンド。
- `touch -t [[CC]YY]MMDDhhmm[.ss]` で指定したタイムスタンプに変更できる。
- `touch hoge` でファイルが存在していない場合は0サイズのファイルを作成する事ができる。

#### pdcopy

- `pdcoby` で、ターミナルの出力をクリップボードにコピーしてくれる
  - 入力を終える場合は`Ctrl +D`
  - `cat ~/.ssh/id_rsa.pub | pbcopy` とかで利用すると便利。

### Storybookについて

- React / Raact Native / Vue向けのUI開発環境。
- サンドボックス環境を構築してコンポーネントの挙動やコンポーネントを一望できる

#### 使いみち

- 自作コンポーネントのライブラリー（一覧）や状態込みのスタイルガイド
- ページの作成中、適切なコンポーネントを素早く選び出す
- 開発中・開発後にコンポーネントの UI をテストする
- コンポーネントや API のドキュメント
- エンジニアやデザイナー間のコミュニケーション
- アプリケーションの仕様書
- 参考 : https://storybook.js.org/examples/

### npxについて

- Node.jsを8.2.0以上にアップデートすると利用する事が可能。
- できる事
  - `npm i` で インストールしたパッケージを `npx {パッケージ名}` で実行する事が可能。
- これまでの実行方法
  1. `./node_modules/.bin/(パッケージ名)` で実行
  2. `$(npm bin)/(パッケージ名)` で実行
  3. package.jsonにnpm-scriptを記述して実行
- おまけ
  - ローカルにインストールしていないパッケージを`npx {パッケージ名}` で実行する事が可能（↓こんなかんじ）

```
$ npx cowsay nyarnしか書けねえ体にしてやろうか！

npx: 10個のパッケージを2.106秒でインストールしました。
 _____________________________________
< nyarnしか書けねえ体にしてやろうか！ >
 -------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

### Webpackについて

- モジュールバンドラーとは、モジュールをひとまとめにするツールであり、JSのモジュール各種をまとめて依存関係を解決してひとつのファイルにしてくれるツール。
- もともとはNode.jsの`require()`というモジュール読み込みの仕組み。

#### Entry

- 読み込みを行うモジュールの 依存関係を解決する為のエントリポイント

#### Output

- バンドルされたファイルのアウトプット先。
- 出力先は絶対パスじゃないとだめ。

### requireの歴史

#### CommonJS

- JS便利だからブラウザ以外でも使おうぜ。サーバサイドとか。
- でもブラウザ上で動かす為のものだから動かないよね。
- 困るから、ServerSideの標準仕様を定めようぜ → commonJS
- 外部ライブラリの参照は各JSをモジュール化して、`require()`で読み込みしよう → commonJSの仕様として出てきた。

#### Node.js

- サーバサイドでJSを利用できるようにしたもの。
- `require()` は独自拡張されたらしい。
- `npm install` したパッケージは `require()` で読み込む事が可能。

#### RequireJS

- クライアントサイドでも`reauire()`を使う為に作られたライブラリ。

#### WebPack

- RequireJSをもっと強くしたもの。
- `reauire()` の対象範囲をJSのモジュールだけではなく、
  - altJSのコンパイル
  - CSS / HTMLファイル取り込み
  - JSファイルの取り込み
- 参考  : [require()とは何か？何が便利なのか - Qiita](https://qiita.com/uryyyyyyy/items/b10b012703b5396ded5a)

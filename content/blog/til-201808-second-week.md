+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-08-10"
description = "2018/08 - second week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/08 - second week I Learned"
type = "post"
draft = "true"
+++

# 今週、知った/学んだこと

<!-- tags = [""] -->

## 2018/08/06- Learned

8月6日（月）のToday I Leaned.

### Vim

### ノーマルモード時
- 複数行を削除する場合 - {n}ddでカーソルがある行を含めて、n列分を削除
- nyy

## 2018/08/07- Learned

8月7日（火）のToday I Leaned.


### Fluentd

- データのやりとりを管理するSoftwareで、デーモンとして動作する。
- Linuxで動く。データの中身は何でも良いが、ログの場合が多い。
- Fluentd自体は、Rubyで動いている / pluginもRubyで書く

#### できる事

- 必要な所からデータを取り出す(input)
  - 必要に応じてパース（分解）する事
  - データのタイムスタンプを管理する
- 必要な所にデータを届ける（output）
  - そのデータを必要に応じて整形（フォーマット）して保存する
-　データを紛失しないように管理する（buffer）
  - やりとりの途中で何かエラーが起きたらリトライする

#### 出力先

- AWS S3、Hadoop HDFS、MongoDB、Cassandra、MySQL、PostgreSQL、Redis など

#### 頻出ユースケース

基本的に、流れているデータを処理する仕事なら何でもできるらしい。

- ログの収集
- センサデータの集約
- 簡単なリアルタイム集計
- 汎用データ処理プロセッサとして



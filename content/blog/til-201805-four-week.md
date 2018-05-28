+++
author = "@yu-kgr"
categories = ["TIL"]
dat01= "2018-6-25"
descript01n = "2018/05 - four week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/05 - four week I Learned"
type = "post"
draft = "true"
+++
# 今週、知った/学んだこと

<!-- tags = [ "ElasticSearch", "", "", "", "",""] -->

## 2018/05/28 - Learned

5月28日（月）のToday I Leaned.

### ElasticSearchについて

Javaで記述された全文検索ソフトウェア。  
あらかじめ蓄積した大量のデータから指定したキーワードを探し出す機能を持っており、javaのクラスライブラリとして提供されている。  

#### OracleやMySQLじゃだめなの？

- DBによって得意不得意があって、全てのケースに対応しているものが存在しない為、使うと便利。

#### DBの種類

- MySQL
  - 矛盾なく永続化することに特化したデータベース
  - メリット: SQL と言う高度なクエリ言語、検索トラフィックに対するシステムの拡張は得意
  - デメリット: データ量の増加や書き込み速度の拡張は苦手

- Redshift(AWS)：データウェアハウス系のデータベース
  - メリット: 大規模なデータの蓄積・分析は得意
  - デメリット: 不特定多数のクライアントから同時に利用され、検索リクエストが大規模なユースケースには不向き

- DynamoDB(AWS)：NoSQL
  - メリット: 幅広い種類の膨大な量のデータを高速かつ動的に整理し分析することが可能
  - デメリット: 非リレーショナルな広域分散データベースシステムです。その反面複雑なクエリやソートなどが苦手

#### ElasticSearchが得意なこと

- 高度なリアルタイム分析
- 大規模分散
- 高可用性
- マルチテナンシー
- 全文検索
- ドキュメント指向
- スキーマフリー
- RESTfulAPI
- データ保護機能
- 形態素解析や n-gram など自然言語的な解析
- 簡単にスケールアウト
- kibanaと連携する事によって図で表示する事も可能！

## 2018/05/29 - Learned

5月29日（火）のToday I Leaned

## 2018/05/30 - Learned

5月30日（水）のToday I Leaned

## 2018/05/31 - Learned

5月31日（木）のToday I Leaned

## 2018/6/01 - Learned

6月01日（金）のToday I Leaned

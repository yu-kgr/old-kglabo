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
draft = "true"
+++

# 今週、知った/学んだこと

<!-- tags = ["IAM", "CloudTrail", "料金アラート", "料金の見積"] -->

## 2019/09/03- Learned

9月3日（月）のToday I Leaned.

- aaa

## 2019/09/04- Learned

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

<!--

## 2019/09/05- Learned

09月05日（水）のToday I Leaned.

- ccc

## 2019/09/06- Learned

09月06日（木）のToday I Leaned.

- ddd

## 2019/09/07- Learned

09月07日（金）のToday I Leaned.

- eee

---

## 今週の感想

- fff

-->

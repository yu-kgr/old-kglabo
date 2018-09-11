+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-01-01"
description = "2018/09 - second week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/09 - second week I Learned"
type = "post"
draft = "true"
+++

# 今週、知った/学んだこと

<!-- tags = ["DB"] -->

## 2018/09/10- Learned

09月10日（月）のToday I Leaned.

### データベース設計について

1. 概念設計
  a. 実態・関連図（ESR図）

## 2018/09/11- Learned

09月11日（火）のToday I Leaned.

「[手を動かしながら2週間で学ぶ AWS 基本から応用まで](https://www.udemy.com/aws-14days/)」  
Day3 - VPCを使ってネットワークを構築する

### VPCを作る

- public サブネット
- Internet GWも一緒に作成する

### Webサーバ用 EC2の作成

- VPCやサブネットを指定

### Webサーバ用 EC2の設定

- OS初期設定
- ミドルウェアのインストール
- Githubに用意しているサンプルコードを動かす


### MEMO: sshでec2に入ろうとしたらErrorが出た

```shell
$ ssh -i ~/.ssh/***.pem ec2-user@***.***.***.***
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0444 for '/Users/NAME/.ssh/***..pem' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "/Users/NAME/.ssh/***..pem": bad permissions
ec2-user@***.***.***.***: Permission denied (publickey,gssapi-keyex,gssapi-with-mic).
$ chmod 0600 ~/.ssh/***.pem
$ ssh -i ~/.ssh/***.pem ec2-user@***.***.***.***
```

- Permissionを0600にしてあげないとだめっぽい
- `$ chmod 0600 ~/.ssh/***.pem` で変更してあげたら問題なく行けた。


## 2018/09/12- Learned

09月12日（水）のToday I Leaned.

- ccc

## 2018/09/13- Learned

09月13日（木）のToday I Leaned.

- ddd

## 2018/09/14- Learned

09月14日（金）のToday I Leaned.

- eee

---

## 今週の感想

- fff

+++
author = "@yu-kgr"
categories = ["TIL"]
tags = [""]
date = "2018-10-13"
description = "2018/10 - Thaad week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/10 - Thaad week I Learned"
type = "post"
draft = "true"
+++

# 今週、知った/学んだこと

## 2018/10/15- Learned

10月15日（月）のToday I Leaned.

### MVCについて

いつも「ModelとかControllerって何するんだっけ？」という事になってしまうので、改めて📝する。

- Model-View-Controllerの略でMVCと呼ぶアーキテクチャ(1.)

|名称|役割|
|---|---|
| Model | ビジネスロジックを記述する(2.) |
| View | Modelを表示する |
| Controller | Viewの入力を受け取って判断し、Modelを起動する |

1. Viewへの入力を受ける
2. Controllerが受け取った内容をModelに渡す
3. Modelが内容を処理して、Viewを返す


#### キーワード

1. ビジネスロジック ... システムにおけるあれこれの処理の事
2. アーキテクチャ ... 構造・構成の事

## 2018/10/16- Learned

10月16日（火）のToday I Leaned.


## ファネル分析

{{< img-post path="date" file="img-funnel.png" type="left" >}}

商品購入や会員登録などアプリ内でユーザーにしてほしいアクションに至るまでのプロセスの離脱率を把握し、どこで多くのユーザーが離脱しているかを確認する分析手法。  
分析結果のグラフが漏斗（ファネル）状になる事から、そう呼ばれる。

## 2018/10/17- Learned

10月17日（水）のToday I Leaned.

### テストカバレッジとは

- でき上がったプログラムのテストをする際に、どの程度をテスト対象とする(ことができる)かをカバレッジ(テストカバレッジ)
  - 範囲の定義の仕方によりいくつかの種類があり、命令全体のうちテストできるものの比率を「ステートメントカバレッジ」(命令網羅率)
  - コード内の分岐のうちテストできるものの比率を「ブランチカバレッジ」(分岐網羅率)
  - コード内に記述された条件のうちテストできるものの比率を「コンディションカバレッジ」(条件網羅率)

カバレッジを計測する目的は「テストケースが十分に網羅されていない」コードを限りなく少なくする事で、  
「コードの品質を向上させつつ、潜在的なバグを発見しやすくする」ことが目的。

カバレッジの数値が常に高い場合は、潜在的なバグに対処できるテストが記載されていない可能性があるので、  
テストケースのアンチパターンに該当していないか確認したほうが良いらしい。またカバレッジは85%くらいが努力目標として良いらしい。

- [参考:テストカバレッジ100%を追求しても品質は高くならない理由と推奨されるカバレッジの目標値について](https://qiita.com/bremen/items/d02eb38e790b93f44728)
- [参考:TDD Anti-patterns catalogue at Stack Overflow を簡単に訳してみた](http://joker1007.hatenablog.com/entry/20130709/1373365053)


## 2018/10/18- Learned

10月18日（木）のToday I Leaned.

### figma チュートリアルやった📝

- figmaでできる事

1. レイヤーに対してエフェクトを付与できる  ![figma-imageEffect](/blog/til-201810-thaad-week/images/figma-imageEffect.png)
2. GoogleFontを利用する事ができる  ![figma-googleFont](/blog/til-201810-thaad-week/images/figma-googleFont.png)
3. パスをいじってベクターベータを編集できる  ![fagma-vectorEdit](/blog/til-201810-thaad-week/images/fagma-vectorEdit.gif)
4. デバイスサイズに乗じたフレームを作成（任意サイズも可）できる  ![fagma-frameCreate](/blog/til-201810-thaad-week/images/fagma-frameCreate.gif)

## 2018/10/19- Learned

10月19日（金）のToday I Leaned.

### hoge

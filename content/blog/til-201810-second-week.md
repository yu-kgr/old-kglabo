+++
author = "@yu-kgr"
categories = ["TIL"]
tags = ["iOS/Chrome", "Linux Command"]
date = "2018-10-12"
description = "2018/10 - Second week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/10 - Second week I Learned"
type = "post"
draft = "false"
+++

# 今週、知った/学んだこと

## 2018/10/09- Learned

10月09日（火）のToday I Leaned.

### iOS 12+Chrome 69でバグがあるっぽい

2018/10/09現在、iOS 12+Chrome 69で`<input type="file>`を利用した場合、  
にChromeがクラッシュしてしまう模様 / [Googleのフォーラムで同様の報告が8/12にされている模様](https://productforums.google.com/forum/#!topic/chrome/DAyZf0GM6Yg)

#### 実際に検証してみた（できる範囲で）

- [Ajax/imgUpload Test: Codepen](https://codepen.io/yu-kgr-the-sans/pen/GYrvWg)
- [FileReader.readAsDataURL Test: Codepen](https://codepen.io/yu-kgr-the-sans/pen/NOdwWJ)
- [<input type="file">& confirm method Test: Codepen](https://codepen.io/yu-kgr-the-sans/pen/pxRpyP)

#### 結果

実機検証してみた所、

- iOS8 + Chrome 47 - 問題はなし
- iOS10 + Chrome 69 - 問題はなし
- iOS12 + Chrome 69 - 問題が発生

html上で、<input type="file">を利用する or JS側で関連するメソッドを利用した場合、  
Chromeが高確率でクラッシュする事がわかった。Chromeさん頑張って…！

## 2018/10/10- Learned

10月10日（水）のToday I Leaned.


### Linux Command / Pipe

- こいつをパイプと呼ぶ → `|`
- 何かしらの処理の後に `|` を挟む事で、前で行った処理の内容を後の処理にわたす事ができる

たとえば、下記のようなファイルがあったとした場合

```
# message.log
tanaka : You are stupid!
tanaka : You are stupid!
tanaka : You are stupid!
tanaka : You are stupid!
tanaka : You are stupid!
tanaka : You are stupid!
tanaka : You are stupid!
tanaka : You are stupid!
tanaka : You are stupid!
tanaka : You are stupid!
tanaka : I am a genius!
```

1. message.logの内容から、'tanaka'という単語の数を数える

```
$ cat message.log | grep 'tanaka' -c
$ 11
```

2. 'tanaka'という単語が含まれた文字列から、'You are stupid'と記載された回数を取得

```
$ cat message.log | grep 'tanaka' | grep 'You are stupid' -c
$ 10
```

3. 同様に、'tanaka'という単語が含まれた文字列から、'I am a genius'と記載された回数を取得

```
$ cat message.log | grep 'tanaka' | grep 'I am a genius' -c
$ 1
```

4. 2の内容をresult.txtファイルとしてアウトプット
```
$ cat message.log | grep 'tanaka' | grep 'You are stupid' >! result.txt
```

こんな感じの使い方ができる。
```

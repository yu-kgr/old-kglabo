+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2017-11-30"
description = "JavaScriptの学習。「DOMオブジェクト」について"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "date"
linktitle = ""
title = "TIL - JavaScript - DOMオブジェクトについて"
type = "post"
+++

## JavaScript - DOMオブジェクトについて
JavaScriptでWebサイトを動的に書き換えるには、Document Object Model（DOM）という仕組みを利用する

## Document Object Model（DOM）とは
JavaScriptで記述されたプログラムから、HTMLページにアクセスして、HTMLページを操作する方法を提供している。

## DOMツリー
DOMツリーとは、HTMLドキュメントやXMLドキュメントをツリー構造として表現したもの。

```html
<!DOCTYPE html>
<head>
  <title>Document</title>
</head>
<body>
<h1>大見出し</h1>
<h2>中見出し</h2>
<p>DOMツリーとは、HTMLドキュメントやXMLドキュメントを<strong>ツリー構造</strong>として表現したもの。</p>
</body>
</html>
```

* Document
  * `<html>`
    * `<head>`
      * `<title>` - Document
    * `<body>`
      * `<h1>` - 見出し
      * `<h2>` - 見出し
      * `<p>` - DOMツリーとは、HTMLドキュメントやXMLドキュメントをツリー構造として表現したもの。
        * `<strong>` - ツリー構造

## ノード

文章を構成する要素、属性、テキストといったオブジェクトをノードと呼ぶ。

* 要素ノード
* 属性ノード
* テキストノード

## DOM仕様策定について

* DOMの仕様は、Level1~4がW3Cにより策定。
  * W3Cとは、WEBで使用される各種技術の標準化を推進する為に設立された団体。
* 最新版は、WHATWG（Web Hypertext Application Technology Working Group）というコミュニティーがLiving Standardとして定義。
  * Living Standardとは常に改良が加えられているゆるい規格のようなもの。

## ブラウザオブジェクトの階層構造

* window
  * screen
  * document
  * location
    * form
      * Element
    * anchor
    * Images
  * navigator
  * history

## window オブジェクト

* ブラウザを操作するための機能を集めたオブジェクト
* ブラウザオブジェクトの階層構造の最上位に位置する

## document オブジェクト

* Windowオブジェクト内に表示された、HTMLで表現されているコンテンツを保持しているオブジェクト
* Window内に表示されたドキュメントを操作するのは、Documentオブジェクトの役割。

## Location オブジェクト

* 現在表示されているページのロケーションに関する情報を提供する
* 現在の表示URLアドレスに関する情報を取得できる


## history オブジェクト

* ブラウザの履歴の操作
* 画面上に表示しているページの移動などの操作

## Navigator オブジェクト

* ブラウザ名やバージョンなど、ブラウザ固有の情報を提供する

## screen オブジェクト

* ディスプレイに関する情報を提供する

## form オブジェクト

* Formに関する情報を提供
* Formの操作

## Anchor オブジェクト

* ページ上のアンカー（`<a>`）に関する情報を取得できる

## Images オブジェクト

* 画像に関する情報の提供
* 画像を操作する機能の提供

## Elements オブジェクト

* HTMLドキュメントやXMLドキュメントにおける、要素（タグ）の事
* 例

```html
<p>hogefuga</p>
```

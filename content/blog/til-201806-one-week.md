+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-06-08"
description = "2018/06 - one week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/06 - one week I Learned"
type = "post"
draft = "false"
+++

# 今週、知った/学んだこと

<!-- tags = [ "JavaScript", "プロトタイプ", "UJIターン", "オブジェクト指向", "プロトタイプチェイン", "ECMA Script", "prototype", "__proto__", "AWS", "IAM", "チェンジマネジメント", "レンダリングエンジン", "JavaScriptエンジン"] -->

## 2018/06/04 - Learned

6月4日（月）のToday I Leaned.

### ターン現象の種類

#### 下記をまとめてUJIターン現象というらしい

- Uターン現象: 地方から都市へ移住したあと、再び地方へ移住
- Jターン現象: 地方から大規模な都市へ移住したあと、地方近くの中規模な都市へ移住
- Iターン現象: 地方から都市へ、または都市から地方へ移住

### JavaScript

#### プロトタイプベースのオブジェクト指向言語

- オブジェクト指向言語と総称されるプログラミング言語のうち、**プロトタイプを基礎（ベース）として**オブジェクトを取り扱うもの。インスタンスベースとも呼ぶ。一方、クラスでおこなっているものをクラスベースとよぶ。
  - クラスベースは、オブジェクトの雛形として必ずクラスが存在。クラスをインスタンス化する事でオブジェクトが生成される。
  - プロトタイプベースは、既存のオブジェクトを元（プロトタイプ）として、ユニークな特徴を付与する事で存在する。要は新しいオブジェクトを生成した時点で、すでに別のオブジェクト（プロトタイプ）を元に作られているという事。
- javaScriptはプロトタイプベースでオブジェクト指向を実現している言語。
  - ES2015でクラス構文が実装されて、クラスベースっぽくコードを記載する事ができるようになったが、これは糖衣構文（シンタックスシュガー）であり、プロトタイプベースの言語である事に変わりはない。
- [参考:プロトタイプベースとは](https://ja.wikipedia.org/wiki/%E3%83%97%E3%83%AD%E3%83%88%E3%82%BF%E3%82%A4%E3%83%97%E3%83%99%E3%83%BC%E3%82%B9)
- [参考:プロトタイプベースのオブジェクト指向言語が広く使われていない理由は?](https://teratail.com/questions/77753)

- 厳密に言うと、JavaScriptは他のプロトタイプベースのオブジェクト指向言語と比較すると特殊らしく、その表現も少し異なるらしいが一般的にはプロトタイプヘースのオブジェクト指向言語と呼ばれている。
- [参考:JavaScriptはプロトタイプベースのオブジェクト指向プログラミング言語ではない！？](http://jsstudy.hatenablog.com/entry/2017/03/29/181613)

#### プロトタイプチェインとは

- 自身のオブジェクトにないメソッド（機能）/ プロパティ（属性）を `__proto__` に格納されている別のオブジェクトから連鎖的に検索して呼び出す仕組み。
- 別のオブジェクト（プロトタイプ）にお願い（移譲）して特性（機能・属性）を持ってくる。
-[参考:最強オブジェクト指向言語 JavaScript 再入門！](https://www.slideshare.net/yuka2py/javascript-23768378)

``` JavaScript
// 元となるオブジェクト（プロトタイプ）
var objA = {
  name: 'Taro',
  say: function(){
    console.log(this.name + 'is My Dog');
  }
}

var objB = { name: 'Pochi'};

// プロトタイプを参照
objB.__proto__ = objA; // __proto__でのアクセスは非推奨
objB = Object.create(objA); // こっちが推奨

// プロトタイプを参照
var objC = {}; // __proto__でのアクセスは非推奨
objC.__proto__ = objB; // こっちが推奨

objC.say(); // Pochi is My Dog
```


#### プロトタイプ系のキーワード

- ややこしい。

##### プロトタイプ

- 仕様上の概念 / 仕組みそのものを示す
- 全てのオブジェクトは内部プロパティ`[[Prototype]]`を持つ。

##### prototype

- 関数式（function）で生成されるオブジェクトが持つプロパティのこと
- 最上位の`Object.protorype`までプロパティを探索する特性をもつ。
- `prototype`プロパティには何らかのオブジェクトが格納されている
- **プロトタイプチェインでは利用されない。**


##### __proto__

- Object.prototypeから継承されるアクセサメソッド
  - アクセサメソッドとは、オブジェクト内部のメンバ変数(属性、プロパティ)に外部からアクセスするために用意されたメソッドで、メンバ変数をオブジェクト内部に隠蔽し、外部から直接参照させないようにする。
- 最上位の`Object.prototype.__proto__`までプロパティを探索する
- `Object.prototype`の`__proto__`は`null`
- new でインスタンスを生成したとき、関数（コンストラクタ）の prototype へのアドレスを格納する
- **プロトタイプチェインでは利用されるけど、呼び出し時は非推奨**

#### ECMA Scriptについて

- ざっくり言うと、**標準化されたJavaScriptのバージョン**。
- [参考:ECMAScriptとは何か？](https://azu.github.io/slide-what-is-ecmascript/)

#### ES.next

次期ECMAScriptの事をECMAScript nextや、ES.nextと言ったりするらしい。

## 2018/06/05 - Learned

6月5日（火）のToday I Leaned

- 死んでました。最近、目を酷使しすぎての死亡パターンが多いので対策を考えたい。

## 2018/06/06 - Learned

6月6日（水）のToday I Leaned

### AWS

#### IAM設定について

- rootユーザーで触り続けるのも危険なので、適切な権限を付与したIAMユーザー及びグループを作成したい。
- [参考:最初の IAM 管理者のユーザーおよびグループの作成](https://docs.aws.amazon.com/ja_jp/IAM/latest/UserGuide/getting-started_create-admin-group.html)

### チェンジマネジメント

- 組織を変える基本・変革を成功させるチェンジ・マネジメントに必要な要因。

1. Vision（先への見通し・構想）
  - 「Vision（先への見通し・構想）」がない場合は「CONFUSION（混乱）」が起きる。
2. Skills（技術）
  - 「Skills（技術）」がない場合は「ANXUETY（不安）」が起きる。
3. Incentives（人々の意思決定や行動を変化させるような要因）
  - 「Incentives（人々の意思決定や行動を変化させるような要因）」がない場合は「RESISTANCE（抵抗）」が起きる
4. Resources（資産、財産）
  - 「Resources（資産、財産）」がない場合は「FRUSTRATION（失望）」が起きる
5. ActionPlan（行動計画）
  - 「ActionPlan（行動計画）」がない場合は「FALSE SATRT（誤った開始）」が起きる

- 上記の要因が全てあれば、正しくチェンジしていく事が可能。
- このtopicについては「経営学 / ミクロ経済」などが該当するらしい。


### JavaScript

#### プロトタイプについて

- prototype継承を利用したClass的実装を行った事がない方は、あまり意識した事がない可能性があるらしい。
- オブジェクトのプロパティとしてもメソッドは実装できてしまう為、prototypeでなければいけないということは原則無い
- ただし、ネイティブのメソッドや、他人が作ったオブジェクトのメソッド参照する時に、prototypeで遡ると、そのオブジェクトがどういう機能を有しているか認識できるというメリットがある。
- [参考:WebModulePattern（ES5でのプロトタイプ継承 - ベストプラクティス）](https://github.com/uupaa/WebModule/wiki/WebModulePattern)

#### オブジェクトの生成

- new演算子とコンストラクタ関数によるオブジェクト生成。
- JavaScriptにおけるオブジェクト生成でよく見られるコード

1. コンストラクタ関数の定義を行う
2. prototypeの拡張を行う
3. 上記で用意したものを利用する

```JavaScript
(function(){

// 1. コンストラクタ関数の定義
var Person = function (name) {
  this.name = name;
}

// 2. prototypeの拡張
Person.prototype.name = 'nanashi';
Person.prototype.say = function() {
  console.log('こんにちわ。私は' + this.name + 'です。');
}
/* 1+2で下記のPerson.prototypeオブジェクトが作成される *//*
Person {
 prototype : {
   name: 'nanashi',
   say: function(){
     console.log(..（省略）..);
   }
 }
}*/

// こんな感じで呼び出し可能
console.log(Person.prototype.name); // "nanashi"
Person.prototype.say(); // "こんにちわ。私はnanashiです。"

// 利用
var japanese = new Person('Tanaka');
// 下記のような初期化が行われる

/*
//1. 新しいオブジェクトの生成
var japanese = {};

//2. プロトタイプのオブジェクトの参照を代入
// Person.prototypeオブジェクトの機能が、japaneseで利用できるようになる
japanese.__proto__ = Person.prototype;

//3. japaneseをthisに、コンストラクタ関数を実行
Person.apply(japanese, ['Tanaka']);

//4. 完成したオブジェクトを返す
return japanese;

---

// 結果として、新しいオブジェクト japanese の __proto__は、
// Person.prototypeに入っているオブジェクトの参照を持つ

japanese: {
  name: 'Tanaka'
  __proto__: {
    name: 'nanashi'
    say: function(){...} // ※①
  }
}

*/

// Person.prototype が japanese.__proto__に代入された直後の為、同一性比較はtrue
console.log(japanese.__proto__ === Person.prototype); // true

// Callされるが、japanese上にはsayがない為
// __proto__を遡り、上記（※①）のsayを見つける。
// name は japanese上で見つける。
japanese.say(); // "こんにちわ。私はTanakaです。"

japanese.name = 'Satou'; // japanes e のnameを更新
japanese.say(); // "こんにちわ。私はSatouです。"

Person.prototype.name = 'Suzuki'; // Person.prototype.nameを変更
japanese.say(); // "こんにちわ。私はSatouです。"
// name は japanese で見つかるので結果に変更はない

delete japanese.name; // japanese自身のnameを削除
japanese.say(); // "こんにちわ。私はSuzukiです。"
// japanese自身がnameを持っていない為、say / name 共に __proto__から検索される

})();

```

##### __proto__

- プロトタイプチェインで検索されるプロトタイプオブジェクトが入っている。
- **プロトタイプチェイン**で利用されるもの

##### prototype

- プロトタイプオブジェクトの控室
- newとコンストラクタ関数でオブジェクトを生成する際、`__proto__`に代入される。
- **オブジェクト生成**で利用されるもの

## 2018/06/07 - Learned

6月7日（木）のToday I Leaned

### ES2015

#### class構文

- 前日のptrototypeでのオブジェクト指向実装をclassに置き換えしてみる

```JavaScript
var Person = function(name) {
  this.name = name;
}
Person.prototype.


---

class Person {
  constructor (name) {
    this.name = name;
  }
  say(){
    console.log(`こんにちわ。私は ${this.name} です。`);
  }
}

var japanese = new Person('Tanaka');
japanese.say();
```

- ES5の時、prototypeの場合はnameメソッドをPeson関数に追加しているが、同様の事をclassでやるときってどうするのか？
- そもそもPersonをインスタンス化しないで追加したnameメソッドを参照できるのにClassの場合は同様の事が出来ない？
  - classの場合は、インスタンス化せずに呼び足す場合は`static` メソッドを活用する他ない。
  - prototypeは割となんでもあり感が強いので、オブジェクトのプロパティにしてしまうとか。


## 2018/06/08 - Learned

6月8日（金）のToday I Leaned

### JavaScript

#### thisの性質について

- thisは特別な変数であり、利用される場所や呼び出し方によって中身が変化する。

1. 関数コール時にその関数が所属していたオブジェクトが`this`になる。
2. ただの関数で呼び出しした場合は、所属しているオブジェクトがないので、グローバルオブジェクトを呼出（ブラウザの場合は`windows`オブジェクトが呼出）

#### thisの性質を操る方法

- thisは標準的な利用方法だと上記の使い方になるが、呼び出し元でthisを操る事が可能メソッドが存在する
- 関数オブジェクトにはthisをコントロールする事が可能な3つのメソッドが存在する（関数オブジェクトのみ）

##### callメソッド

- こんなかんじ。

```JavaScript
call(
  object, // objectが関数内でのthisになり
  arg1, atg2, ... // その後の引数は関数呼び出し時に与える引数になる
  )
```

- callとapplyは関数を実行する

```JavaScript
var Person = function(name){
  this.name = name;
}

function say(arg1, arg2){
  alert(arg1 + this.name + atg2);
}

var person = new Person('Tanaka');

// callの第一引数がthisになり、第二引数以降がsay関数の引数になる
say.call(person, 'Hello','san');
```

- 関数はオブジェクトに束縛されていない為、他のオブジェクトのメンバ（ローカル変数）だったとしても関係がない

##### applyメソッド

- こんなかんじ

```JavaScript
apply(
  object, // objectが関数内でのthisになり
  Array // その後の因数は関数呼び出し時に与える因数になる
  )
```

- callとapplyは関数を実行する


```JavaScript
var Person = function(name){
  this.name = name;
}

function say(arg1, arg2){
  alert(arg1 + this.name + atg2);
}

var person = new Person('Tanaka');

// applyの第一引数がthisになり、第二引数以降がsay関数の引数になる
say.apply(person, ['Hello','san']);
```

- 関数はオブジェクトに束縛されていない為、他のオブジェクトのメンバ（ローカル変数）だったとしても関係がない


##### bindメソッド

```JavaScript
bind(
  object, // objectが関数内でのthisになり
  arg1, atg2, ... // その後の因数は関数呼び出し時に与える因数になる
  )
```

- bindは関数に値を束縛する

```JavaScript
var Person = function(name){
  this.name = name;
}

function say(arg1, arg2){
  alert(arg1 + this.name + atg2);
}

var person = new Person('Tanaka');

var say2 = say.bind(person); // personをthisにthisに束縛した新しい関数オブジェクトを返す
say2('Hello ', 'san') // say2関数の呼び出しでは常にpersonがthisになる。
```

#### JavaScriptエンジン

- 主要なブラウザのレンダリングエンジンとJavaScriptのエンジンは2018/06現在は下記の通り。

##### Google Chrome

- レンダリングエンジン : Blink
- JavaScriptエンジン : V8

##### Safari

- レンダリングエンジン : Webkit
- JavaScriptエンジン : JavaScriptCore

##### Firefox

- レンダリングエンジン : Gecko
- JavaScriptエンジン : SpiderMonkey

##### Internet Explorer

- レンダリングエンジン : Trident
- JavaScriptエンジン : Chakra

---

### 雑感

今週は、JavaScriptのObjectやprototypeベースでのオブジェクト指向、__proto__やプロトタイプチェイン。  
prototypeを利用したクラスの作成方法について学習。合わせてES2015のclass構文について少々。

別途、Reactのチュートリアルを進行中。

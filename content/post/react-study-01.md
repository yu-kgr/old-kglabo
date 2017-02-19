+++
date = "2017-02-18T00:37:13+09:00"
draft = "false"
thumbnail = "images/2017/02/react-study.jpg"
tags = ["React","ES2015","Today I learned"]
categories = ["Develop"]
title = "TIL - ReactStudy#01"

+++
## 概要
[React基礎](http://basic-react.axlight.com/html/)を参考にしての学習。

## 参考にしたサイト
* [React基礎](http://basic-react.axlight.com/html/)
* [生のReactを知ろう – JSX、Flux、ES6、Webpackを使わず…](http://postd.cc/learn-raw-react-no-jsx-flux-es6-webpack/)


## 学習内容

以下、[React基礎](http://basic-react.axlight.com/html/)より引用（個人用メモ）


### 前置き

Reactでコーディングする先は、**ES2015(ES6)**を使うと便利になる。  
んで、ES2015を利用する際は**トランスパイル**が必要。  
後々、**JSX** を使うし相対的にES2015の敷居下がるよね？ 覚えよ？って記載されてた。


* **ES2015(ES6)** - [コチラ](http://qiita.com/tuno-tky/items/74ca595a9232bcbcd727)によると、*ECMAScript6thEdition* == *ES6* の事。
  * 当初は ES6の名前で発表されたらしいが、正式名称が*ECMAScript2015*になった事もあり、ES2015と呼ばれているとの事
* **トランスパイル** - ソースコードからソースコードへのコンパイル
* **JSX** - [コチラ](http://qiita.com/ConquestArrow/items/29fc478f48862a4d14fb)によると、ReactのJXSとAltJSのJSXとAdobeJSXがあるらしい 
  * つまりどういうことだってばよ？


### ES2015について

ES2015でよく使う文法についての解説されていた。

#### const/let

* `const` - 再代入しない  
* `let` - 再代入できる 

```
const x = 1;
let y = 2;
y = 3;

const z = { a: 4, b: 5 };
z.a = 6;
```

`var`は消えた模様。

---

#### object shorthand

* オブジェクトのプロパティ名と値の変数名が同じ場合、省略記法を使える

```
const foo = 'abc';
const bar = { foo }; // same as { foo: foo }
```

---

#### destructuring object

*destructuring assignment* という簡便な記法が利用できる  
特にオブジェクトについての記法を紹介されていた。  
変数への代入だけでなく、関数のパラメータ宣言でも用いられるとの事。

```
const obj = { first: 'Ebisu', last: 'JS' };
const { first, last } = obj;
// first === 'Ebisu', last === 'JS'

function printName({ first, last }) { console.log(first, last); }
printName(obj);

// same as
// function printName(name) { console.log(name.first, name.last); }
``` 

---

#### アロー関数

アロー関数
`() => ...` って言う記法。詳しくは[こちら](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/arrow_functions)  
`this`を一旦置いとくと、アロー関数は通常の関数の省力記法と考える事ができるとの事。

```
const f1 = function(x) { console.log(x); };
const f2 = (x) => { console.log(x); };
// f1 and f2 is almost the same
```

---

`return` 文が一つだけの場合は、文そのものを省略できる

```
const f3 = (x) => { return (x + 1); };
const f4 = (x) => (x + 1);
// f3 and f4 is the same
```

カッコの省略も可能（任意）

```
const f5 = x => x + 1;
```

`Coffee Script`で言うと、 `hoge = ->`みたいなもん？

---

### 関数型のコーディングについて

Reactでコンポーネントを書く際には、**関数型コーディング** の方が楽らしい。  
その前提を前置きした上で、このプログラム中によく使う文法について説明されている。

* **関数型コーディング**  - [関数型プログラミングはまず考え方から理解しよう](http://qiita.com/stkdev/items/5c021d4e5d54d56b927c)


#### pure function
  * 一般的に副作用がない関数

```
const pureFunc = (x) => { let y = x + 1; return y; };

let y;
const notPure = (x) => { y = x + 1; return y; };

const notPure2 = (x) => { console.log('foo'); return x + 1; };
```

---

#### logical operators

論理演算子には `&&` , `||` , `!` の3つがある。

* `x && y` は、xが **falsy** の場合はx、違う場合はyになる
  * **falsy**とは、 `false` , `null` , `0` , `''` などの値。詳しくは[こちら](https://developer.mozilla.org/ja/docs/Glossary/Falsy)
* `x || y` という表現は、 `x` が `falsy` の場合は `y` 、違う場合は `x` になる
* `!x` という表現は、 `x` が `falsy` の場合は `true` 、違う場合は `false` になる
  * `x` は真偽値(boolean)でなくてもよいです

```
0 && 1
// 0

1 && 2
// 2

0 || 1
// 1

1 || 2
// 1

!0
// true

!1
// false
```

---

#### ternary operator

三項演算子はよく使うとの事  
`x ? y : z` は `x` がfalsyの場合はzであり、そうでない場合はyになります。

```
0 ? 1 : 2
// 2

3 ? 4 : 5
// 4
```

---

#### filter

Array.filterは配列から部分配列を作る関数

* [参考](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

引数で与えたテスト関数がtruthy(つまりfalsyでない)を返す要素の配列を返す。  
配列は新しく作られますが、要素はコピーされない。  
テスト関数にはアロー関数を使うと簡便に書くことができます。

```
[1, 2, 3, 4].filter((x) => (x > 2))
// [3, 4]

['a', 'ab', 'abc', 'abcd'].filter((x) => (x.length <= 2))
// ['a', 'ab']

[0, 1, 2, '', 'a', false, true].filter((x) => (x));
// [1, 2, 'a', true]
```

---

#### map

Array.mapは配列から要素ごとに変換して新しい配列を作る関数

* [参考](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

引数で与えられた変換関数で返される値を要素にもつ配列を返します。  
配列は新しく作られる。要素数は変化しない。

```
[1, 2, 3, 4].map((x) => (x * 2))
// [2, 4, 6, 8]

['a', 'ab', 'abc', 'abcd'].map((x) => (x.length))
// [1, 2, 3, 4]

[1, 2, 'a', 'b'].map((x) => ('あ' + x))
// ['あ1', 'あ2', 'あa', 'あb']
```

---

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
draft = "false"
+++

# 今週、知った/学んだこと

<!-- tags = [ "ElasticSearch", "javaScript", "npm script", "webpack", "ES2015","マイクロワイヤーフレーム"] -->

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

#### npm scriptについて

- package.jsonのscriptフィールドにスクリプトを記載すると、コマンドのエイリアスを作成できる。

```json
"scripts" : {
  "build:dev" : "webpack --mode development"
}
```

#### webpack

- [これの続き](https://kglabo.com/blog/til-201805-thaad-week/#webpack%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6)

##### Loader

- Loaderを利用する事で、JavaScript以外のファイルもstaticファイルも同時にbundleする事が可能。
- [いろいろな種類のloader](https://webpack.js.org/loaders/)が存在する


## 2018/05/29 - Learned

5月29日（火）のToday I Leaned

#### webpack

- 上記の続き

##### Plagin

- Loaderはファイルの依存関係であった、モジュールタイプの変更に使えたが、PluginはLoaderで賄えない幅広いタスクの実行が可能になる。
- Pluginを利用する場合は、Moduleをrequireした後、new演算子を使ってインスタンス化する必要がある。

#### ES2015

なんか前にも学習してた気がするけど、間が空いてしまって忘れつつあるので、  
改めて備忘録と後々見返す事を兼ねて記載く。

##### ブロックスコープ

- varは関数定義の`{`と`}`内じゃないとスコープが作られないので、スコープを作りたい場合は即時関数を利用する必要がある。

```JavaScript
// 普通に{}でスコープ作った場合
{
  var a = "foo";
}

if(true){
  var b = "bar";
}

for(var i = 0; i < 1; i++){
  var c = "buz";
}

console.log(a); // "foo"
console.log(b); // "bar"
console.log(c); // "buz"

// 即時関数を作った場合（スコープ作られる）
(function(){
  var a = "foo";
})();

console.log(a); // ReferenceError: a is not defined

```

- let/constは、varとは異なりブロックスコープ（`{`と`}`で囲まれた内部）でしか変数/関数の参照ができない
  - メリット 定義した変数・関数の影響範囲が明確化される

```JavaScript
{
  let   a = "foo";
  const B = "bar";

  console.log(a); // "foo"
  console.log(B); // "bar"
}

console.log(a);
// ReferenceError: a is not defined
console.log(B);
// ReferenceError: B is not defined
```

#### テンプレートリテラル

- 文字列の連結の為に`+`や`concat()`を利用する必要があったが、下記の形で変数名を参照する事が可能。

```JavaScript
const user = { name: 'Taro'};
console.log(\`${user.name}が入室しました。\`); // "Taroが入室しました、"
```

- 計算式を入れる事も可能。変数が存在しない場合は`||`を入れることで分岐される事も可能。

```JavaScript
console.log(\`${user.name||"匿名"}が入室しました。\`); // "匿名が入室しました、"

const user = {name: 'Taro'};
console.log(\`${user.name||"匿名"}が入室しました。\`); // "Taroが入室しました、"
```

#### デフォルト引数

- ES2015からは引数定義の箇所でデフォルト値を設定可能

```JavaScript
function joinChannel(name = "匿名") {
  console.log('${name}さんが入室しました。')
}

// 匿名さんが入室しました。
joinChannel();

// 太郎さんが入室しました。
joinChannel("太郎");
```

#### アロー関数

- 関数定義を省略して書く事が可能。

```JavaScript
// 従来の記法
const add = function (a,b) {
  return a + b;
}

// functionを省略可能
const add = (a,b) => {
  return a + b;
}

// 波括弧とreturnも省略できる場合
const add = (a,b) => a + b;
```

## 2018/05/30 - Learned

5月30日（水）のToday I Leaned

- 理解度に合わせて基礎をいったり来たり。

#### JavaScript

- PrototypeとClass定義について

##### Prototypeについて

- ES2015以前は、classという概念がなかったのでJSの仕様でなんとかclassっぽい事を実現する為に運用でカバーしていたらしい。
- [図で理解するJavaScriptのプロトタイプチェーン](https://qiita.com/howdy39/items/35729490b024ca295d6c)

##### class定義

- これまではクラス定義がなかったのでprototypeにメソッドを追加して対応していた。

```JavaScript
var Parson = function(id, name) {
  this.id = id;
  this.name = name;
}

Paeson.prototype.printName(){
  console.log(this.name);
}

var person = newPerson(1,太郎);
person.printName();

```

## 2018/05/31 - Learned

5月31日（木）のToday I Leaned


#### JavaScript

- prototypeやclass定義の所で一旦、JavaScript自体について知ったほうが良い気がした為一旦もどる。
- 出てくる名称や独自仕様について。

##### イベントとイベントハンドラ

- HTML要素に対してかかる（かける）名をイベントと呼び、そりによって起こる現象をイベントハンドラと呼ぶ。
- <要素名 onイベント名=“イベントハンドラ”></要素名>

###### ホイスティング（巻き上げ）

- JavaScriptには変数を指定した時点、その宣言されたスコープ内で巻き上げ（ホイスティング）という現象が発生する仕様。
  - [参考:関数の場合の変数の巻き上げ問題について](https://qiita.com/cocottejs/items/143f70e806c61ffafe28)
  - [参考:やっとわかったjsの「巻き上げ」](https://qiita.com/39_isao/items/d9d80e98b5bd1938bc1d)

```JavaScript
console.log(x) // ReferenceError: x is not defined（そんなもんねーよ）
```

```JavaScript
console.log(x) // undefined（1かはわからんけど、xは存在してるよ）
var x = 1;

// ↓ 内部ではこんな事（ホイスティング）が起きてる
var x;
console.log(x);
x = 1;
```

##### 関数定義について

- 関数定義の方法が「関数宣言文」と「関数定義式」の二種類ある。
  - 本質的な違いは「式（Expression）」か「文（Statement)」なのかの違い。
  - [参考:ホスティング宣言の巻き上げについて](https://wp-p.info/tpl_rep.php?cat=js-intermediate&fl=r9)
  - [参考:無名関数 関数式と関数宣言](https://wp-p.info/tpl_rep.php?cat=js-intermediate&fl=r10)
  - [参考:【JavaScript】関数定義いろいろ](https://qiita.com/tomcky/items/988fc5f56d019e9dc097)

```JavaScript
// 関数宣言文
function hoge(){
  // ここに処理
}

// 関数定義式（関数リテラル）
var hoge = function (){
  // ここに処理
};
```

- 関数宣言文の場合は、関数宣言の前に関数を実行してもエラーにならない。
- なぜなら、関数宣言文の場合はブラウザでのレンダリングが完了した時点で関数が生成されている為、宣言する前に実行可能。

```JavaScript
// 関数宣言文を実行した場合
hoge(); // 先に呼ばれてるけど "hoge"と表示される

function hoge(){ // 関数宣言した場合は、レンダリングが完了した時点で関数生成済み
  console.log("hoge");
}
```

- 関数定義式（関数リテラル）の場合は、関数定義の前に関数を実行するとエラーになる。
- なぜなら、関数定義式の場合は変数に対して代入処理が行われた時点で初めて関数定義される為、代入後じゃないと実行不可能。

```JavaScript
hoge(); // Uncaught TypeError: hoge is not a function

var hoge = function (){
  console.log("hoge");
};
```

#### マイクロワイヤーフレーム

- マイクロワイヤーフレームという従来のワイヤーフレームを小さく（100px~300pxぐらいでサイズ決める）して良さを濃集したものがあるらしい。
  - [参考:次世代のワイヤーフレーム「マイクロフレーム」とは](http://uxmilk.jp/66066)
  - 効能 : つくるのはやい / わかりやすい / 忠実制が少ないので混乱しづらい

#####  利点

- はやい
  - スケッチと同じくらい早く作ることができる
  - 簡単に作業を繰り返すことができる
  - すぐに結果共有が可能
- わかりやすい
  - プランや要件をわかりやすく伝えることができる
  - 顧客と協力して同じ視点で作業を反復することが可能
  - WFのように捨ててしまう作品に時間をかけすぎない
- 忠実性が低いので混乱が少ない
  - めっちゃ最小化されているので、完成品とのギャップを感じづらい

## 2018/6/01 - Learned

6月01日（金）のToday I Leaned

- なんだか今週はJavaScript Week。

#### JavaScript

- 関数オブジェクトやらコンストラクタ・インスタンス・クロージャ・プロトタイプなど

##### 関数の即時実行と受け渡し

- javaScriptでは関数の即時実行が可能。
- [参考:久しぶりにJavaScriptを思い出す(関数オブジェクト、クロージャ）](https://qiita.com/fewzio/items/a502defb516e75d7e81b)

```JavaScript
// 普通に定義して実行する場合
var a = function(){ console.log("TEST") };
a(); // var aへの参照と実行 "TEST" と表示される
```

```JavaScript
// 即時実行する場合
var a = function(){ console.log("TEST") }(); // var aへの参照と実行 "TEST" と表示される
```

- ただ上記は、aに対して何のリテラルも代入しているわけではないので、`"TEST"`がコンソールに表示された後、`undefined` が出力される。

```JavaScript
// 即時実行する場合
var a = function(){ console.log("TEST") }(); // "TEST"
console.log(a); // aには何も代入されていないのでundefined
```

- a自体に値を代入したい場合は`return`を利用すると戻り値に1が返ってくる。

```JavaScript
// 即時実行する場合
var a = function(){ return 1; }(); // aに1が代入される
console.log(a); // 1
```

- JavaScriptでは関数を値と同じように受け渡しができるので、下記のように戻り値に関数を定義する事も可能。

```JavaScript
// 戻り値を関数にした場合
var a = function () {
  return function () { // 関数を実行した結果、後ろの関数がaに代入される
    console.log("TEST");
  }
}();

a(); // "TEST" & 上記の場合はaには何も代入されていないのでundefined（ややこしい）

```

- `return`内にプロパティを定義したうえで関数を定義する事も可能。

```JavaScript
// 戻り値を関数にした場合
var a = function () {
  return {
    propA: function () { console.log("A"); },
    propB: function () { console.log("B"); },
  }
}();

a.propA(); //"A"
a.propB(); //"B"
```

##### クロージャ

- 関数内部で定義した関数を、代入した変数（オブジェクト）では、中の変数の値も保持し続ける。
- この変数値も保持し続ける関数をクロージャと呼ぶ。プライベート変数みたいなものらしい。

```JavaScript
var module = function() {
  var count = 0; //module関数の中で保持される変数（クロージャ）

  return {
    increment: function() {
      count++;
    },
    show: function() {
      console.log(count);
    }
  };

}();

module.show(); // 0
module.increment(); // countを+1する
module.show(); // 1
```

##### オブジェクト

- [参考:[JavaScript] オブジェクトの基礎](https://qiita.com/yoshi389111/items/245df2d642e49d2acf3a)
- JavaScriptにおけるオブジェクトは、`{key: value}`形式の入れ物（他言語の場合はハッシュテーブルとか連想配列というらしい）で関数も配列もオブジェクト。
- オブジェクトを生成してkey:valueを登録する場合は下記のように行える。

```JavaScript
var obj = new Object();

// "hoge" というkeyに "hello" というvalueを登録
obj.hoge = "hello";

// "func" というkeyに "world" という関数（オブジェクト）を登録
obj.func = function() {
  console.log("world";)
}

// ドット演算子
console.log(obj.hoge); // "hello"
obj.func(); // "world"

// 連想配列風にもアクセス可能
console.log(obj["hoge"]); // "hello"
obj.["func"](); // "world"
```

- valueが関数の場合は`メソッド`と呼び、それ以外のオブジェクトの場合は`プロパティ`と呼ぶ。
- 配列もオブジェクトだけど、特別なプロパティ・メソッドが存在している（[必要な時にggる](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array)）

- ちなみにオブジェクトはオブジェクトリテラルで作成する事も可能
- `{}`は`new Object()`シンタックスシュガー（糖衣構文）

```JavaScript
// new演算子でオブジェクトを作成した例
var obj = new Object();
obj.name = "Taro";

// リテラルでオブジェクトを作成した場合
var obj = {name: "Taro"};
```

##### インスタンスとコンストラクタ

- コンストラクタは関数オブジェクトで、インスタンスはコンストラクタを元に作成された空のオブジェクトの事。
- 関数オブジェクト（コンストラクタ）を元に新しいオブジェクトを初期化して作成（インスタンス化）すると空のオブジェクト（インスタンス）ができる。
- [参考:JavaScriptのクラス？コンストラクタ？？](https://qiita.com/takeharu/items/010752b1427773558f7c)
- [参考:JavaScriptのコンストラクタによるインスタンス生成](http://uxmilk.jp/30348)

```JavaScript
//空のコンストラクタを定義
var Animal = function(){};

//コンストラクタから空のインスタンスを生成
var dog = new Animal();
```


```JavaScript
//コンストラクタを定義
function Animal = function(name,cry){
  this.name = name;
  this.bark = function() {
    console.log(cry);
  };
};

//コンストラクタから空のインスタンスを生成
var dog = new Animal('ポチ', 'ワン');
console.log(dog.name); // "ポチ"
dog.bark(); // ワン

var cat = new Animal('タマ','にゃー');
console.log(cat.name); // "タマ"
cat.bark(); // "にゃー"
```

##### プロトタイプ

- コンストラクタを定義すると、コンストラクタごとに関連付けられた**「プロトタイプオブジェクト」**が暗黙的に作成される。
- 同じコンストラクタから生成されたインスタンスは、プロトタイプオブジェクトを共有する。
- [参考:JavaScript入門 | プロトタイプとは？](http://javascript.keicode.com/lang/prototypes.php)
- [参考:図で理解するJavaScriptのプロトタイプチェーン](https://qiita.com/howdy39/items/35729490b024ca295d6c)


```JavaScript
//コンストラクタを定義
function Animal = function(name){
  this.name = name;
};

var dog = new Animal('ポチ');
var cat = new Animal('タマ');

if (dog === cat) {
  // false
}

if (dog.prototype === cat.prototype) {
  // true
}
```

##### よく使われる謎コード

- [参考:JavaScriptの謎コードまとめ](http://www.f-sp.com/entry/2016/11/18/190732)
  - `!!x` - 二重論理否定の意。二重論理否定には任意の型をBoolean型に変換する副作用がある。Boolean型のへの変更。よく使うらしい。
  - `x||0` - 論理和の意。左辺値をBoolean型として評価して、trueなら左辺値。falseなら右辺値を評価値とする。左か右のどちらかがそのまま返ってくる。よく使うらしい。

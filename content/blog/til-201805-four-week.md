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

- let/constは、varとは異なりブロックスコープ（`{`と`}`で囲まれた内部）でしか変数/関数の参照ができない
  - メリット 定義した変数・関数の影響範囲が明確化される

#### テンプレートリテラル

- 文字列の連結の為に`+`や`concat()`を利用する必要があったが、console.log(\`${user.name}が入室しました。\`)のような形で変数名を参照する事が可能。
- 計算式を入れる事も可能。変数が存在しない場合は、console.log(\`${user.name||"匿名"}が入室しました。\`)という形にする事も可能。

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

#### Prototypeについて

- ES2015以前は、
- [図で理解するJavaScriptのプロトタイプチェーン](https://qiita.com/howdy39/items/35729490b024ca295d6c)

#### class定義

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

## 2018/05/30 - Learned

5月30日（水）のToday I Leaned

- 理解度に合わせて基礎をいったり来たり。

#### JavaScript

JavsSciptで出てくる単語やES2015について...

##### イベントとイベントハンドラ

- HTML要素に対してかかる（かける）名をイベントと呼び、そりによって起こる現象をイベントハンドラと呼ぶ。
- <要素名 onイベント名=“イベントハンドラ”></要素名>

#### ホイスティング（巻き上げ）

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

- [参考:次世代のワイヤーフレーム「マイクロフレーム」とは](http://uxmilk.jp/66066)
- はやい / わかりやすい / 忠実制が少ないので混乱しづらい

#####  利点

- はやい - スケッチと同じくらい早く作ることができる / 簡単に作業を繰り返すことができる / すぐに結果共有が可能
- わかりやすい - プランや要件をわかりやすく伝えることができる / 顧客と協力して同じ視点で作業を反復することが可能 / WFのように捨ててしまう作品に時間をかけすぎない
- 忠実性が低いので混乱が少ない - めっちゃ最小化されているので、完成品とのギャップを感じづらい

###### 備考

- 色以外にコンテンツのマージン等を考える際、他サイトのターゲットユーザを考えた上で参考にすると良さげ。

## 2018/05/31 - Learned

5月31日（木）のToday I Leaned

#### ES2015

## 2018/6/01 - Learned

6月01日（金）のToday I Leaned

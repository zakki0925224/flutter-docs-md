# flutter-docs-md

## Flutter とは

**Flutter** (フラッター)は、Google によって開発された、フリーかつオープンなマルチプラットフォーム開発フレームワークである。全く同じコードで、Android / iOS / Web / Windows/ macOS / Linux といった、さまざまなプラットフォーム向けアプリケーションを開発することができる。
Flutter の開発言語には**Dart**が採用されている。

## Dart 入門

**Dart** (ダート/ダーツ)は、Google によって開発されたコンパイル型言語である。静的型付け、C スタイル構文、マルチパラダイムが特徴であり、Flutter による Web / モバイルアプリ開発などに使用される。

- https://dart.dev/docs/

### 変数

Dart では、`var`、`final`、`const`、型名を使って変数を宣言することができる。

- `var`：型推論で変数を宣言する。
- `final`：一度だけ値を代入できる（再代入不可）。
- `const`：コンパイル時定数として宣言する。
- 型名：明示的に型を指定して宣言する。

```dart
var name = 'Flutter'; // 型推論でString型
final int age = 3;    // int型で再代入不可
const pi = 3.14;      // コンパイル時定数
String message = 'Hello'; // 明示的に型指定
```

#### null 許容型

Dart は null 安全をサポートしており、型名の末尾に`?`を付けることで null を許容する変数を宣言できる。

```dart
int? maybeNumber = null; // nullを許容するint型
String? title;           // nullを許容するString型
```

#### late

`late`修飾子を使うと、変数の初期化を遅延できる（初回アクセス時まで初期化を遅らせる）。

```dart
late String description;
description = 'Dartのlate変数';
```

#### ワイルドカード変数

Dart では、変数名にアンダースコア（`_`）を使うことで「使わない変数」を表現できる。主に一時的な値や無視したい値に利用する。

```dart
var _ = 42; // この変数は使わないことを明示
```

### 演算子

#### 算術演算子

- `+`：加算
- `-`：減算
- `*`：乗算
- `/`：除算
- `~/`：除算の結果を整数で返す
- `%`：除算の余剰

```dart
assert(2 + 3 == 5);
assert(2 - 3 == -1);
assert(2 * 3 == 6);
assert(5 / 2 == 2.5);
assert(5 ~/ 2 == 2);
assert(5 % 2 == 1);
```

#### 等価演算子 / 関係演算子

- `==`：等価
- `!=`：非等価
- `>`：より大きい
- `<`：より小さい
- `>=`：以上
- `<=`：以下

```dart
assert(2 == 2);
assert(2 != 3);
assert(3 > 2);
assert(2 < 3);
assert(3 >= 3);
assert(2 <= 3);
```

#### 型テスト演算子

- `is`：型判定
- `is!`：型否定
- `as`：型キャスト

```dart
var s = 'hello';
assert(s is String);
assert(s is! int);
dynamic d = 42;
int i = d as int;
```

#### 代入演算子

- `=`：代入
- `+=` `-=` `*=` `/=` `~/=` `%=`：複合代入
- `??=`：null の場合のみ代入

```dart
var a = 1;
a += 2; // a = 3
a ??= 10; // aがnullなら10を代入
```

#### 論理演算子

- `!`：論理否定
- `&&`：論理積（AND）
- `||`：論理和（OR）

```dart
assert(!false);
assert(true && true);
assert(true || false);
```

#### ビット演算子 / シフト演算子

- `&`：AND
- `|`：OR
- `^`：XOR
- `~`：NOT
- `<<`：左シフト
- `>>`：右シフト
- `>>>`：符号なし右シフト

```dart
assert((5 & 3) == 1);
assert((5 | 3) == 7);
assert((5 ^ 3) == 6);
assert((~5) == -6);
assert((5 << 1) == 10);
assert((5 >> 1) == 2);
```

#### 条件式

- `?:`：三項演算子（条件式）
- `??`：null 合体演算子

```dart
var result = true ? 'yes' : 'no';
var value = null ?? 'default'; // valueは'default'
```

#### カスケード表記

- `..`：同じオブジェクトに連続して操作を行う
- `?..`：null 安全なカスケード

```dart
var buffer = StringBuffer()
  ..write('Hello')
  ..write(' World');
```

#### スプレッド演算子

- `...`：リストやマップの展開
- `...?`：null 安全なスプレッド

```dart
var list1 = [1, 2, 3];
var list2 = [0, ...list1, 4]; // [0, 1, 2, 3, 4]
var list3 = [0, ...?null, 4]; // [0, 4]
```

### コメント

- `//`: 1 行コメント
- `/** **/`: 複数行コメント
- `///`: ドキュメントコメント

```dart
void main() {
  // print("Hello!");

  /**
  var larry = Llama();
  larry.feed();
  larry.exercise();
  larry.clean();
  **/
}
```

```dart
/// A domesticated South American camelid (Lama glama).
///
/// Andean cultures have used llamas as meat and pack
/// animals since pre-Hispanic times.
///
/// Just like any other animal, llamas need to eat,
/// so don't forget to [feed] them some [Food].
class Llama {
  String? name;

  /// Feeds your llama [food].
  ///
  /// The typical llama eats one bale of hay per week.
  void feed(Food food) {
    // ...
  }

  /// Exercises your llama with an [activity] for
  /// [timeLimit] minutes.
  void exercise(Activity activity, int timeLimit) {
    // ...
  }
}
```

### 型

Dart には、以下のような主な組み込み型がある。

- `int`：整数型
- `double`：浮動小数点数型
- `num`：数値型（`int`と`double`の親）
- `String`：文字列型
- `bool`：真偽値型
- `List`：リスト（配列）型
- `Map`：マップ（連想配列）型
- `Set`：集合型
- `dynamic`：動的型（任意の型を格納可能）
- `Object`：全ての型の基底

```dart
int year = 2024;
double pi = 3.1415;
num anyNumber = 10; // int も double も代入可能
String greeting = 'Hello, Dart!';
bool isActive = true;

List<int> numbers = [1, 2, 3];
Map<String, int> scores = {'Alice': 90, 'Bob': 80};
Set<String> fruits = {'apple', 'banana', 'orange'};

dynamic anything = '文字列もOK';
anything = 123; // int もOK
Object obj = '何でもObject';
```

#### 型推論

`var`や`final`を使うと、右辺の値から型が自動的に推論される。

```dart
var city = 'Tokyo'; // String型と推論される
final price = 1200; // int型と推論される
```

#### 型変換

型変換には`toString()`や`parse()`などのメソッドを利用する。

```dart
int n = int.parse('42'); // 文字列→int
double d = double.parse('3.14'); // 文字列→double
String s = n.toString(); // int→文字列
```

### パターン構文 (`switch`)

Dart の `switch` 文は、値や型に応じて分岐処理を行う。Dart 3 以降ではパターンマッチングもサポートされている。

```dart
var value = 2;
switch (value) {
  case 1:
    print('one');
    break;
  case 2:
    print('two');
    break;
  default:
    print('other');
}

// パターンマッチングの例（Dart 3以降）
Object obj = 'hello';
switch (obj) {
  case int n:
    print('int: $n');
    break;
  case String s when s.length > 3:
    print('long string: $s');
    break;
  default:
    print('other');
}
```

### 制御構文

#### ループ (`for`/`while`/`do while`/`break`/`continue`)

Dart では様々なループ構文が利用できる。

```dart
// for文
for (var i = 0; i < 3; i++) {
  print(i);
}

// for-in文
for (var item in [1, 2, 3]) {
  print(item);
}

// while文
var count = 0;
while (count < 3) {
  print(count);
  count++;
}

// do-while文
int n = 0;
do {
  print(n);
  n++;
} while (n < 3);

// breakとcontinue
for (var i = 0; i < 5; i++) {
  if (i == 2) continue; // 2のときスキップ
  if (i == 4) break;    // 4でループ終了
  print(i);
}
```

#### 分岐 (`if`/`if-case`/`switch`)

条件分岐には `if` 文や `switch` 文が使える。

```dart
var score = 80;
if (score >= 90) {
  print('Excellent');
} else if (score >= 70) {
  print('Good');
} else {
  print('Try harder');
}

// if-case（Dart 3以降）
Object obj = 42;
if (obj is int && obj > 10) {
  print('int and > 10');
}
```

#### エラーハンドリング (`try`/`catch`/`throw`)

Dart では例外処理に `try` / `catch` / `finally` を使う。

```dart
try {
  int result = int.parse('abc'); // 例外発生
} catch (e) {
  print('エラー: $e');
} finally {
  print('終了処理');
}

// 例外を投げる
void check(int n) {
  if (n < 0) {
    throw ArgumentError('nは0以上である必要があります');
  }
}
```

### 関数

Dart では関数もファーストクラスオブジェクトとして扱われ、変数に代入したり、引数として渡したりできる。

```dart
// 通常の関数定義
int add(int a, int b) {
  return a + b;
}

// 短縮構文（アロー関数）
int multiply(int a, int b) => a * b;

// 省略可能引数（デフォルト値あり）
String greet(String name, [String suffix = 'さん']) {
  return 'こんにちは、$name$suffix';
}

// 名前付き引数（{}で囲む、デフォルト値も指定可）
void printInfo({required String name, int age = 0}) {
  print('名前: $name, 年齢: $age');
}

// 無名関数（ラムダ式）
var list = [1, 2, 3];
list.forEach((item) {
  print(item);
});
```

#### 関数型

関数自体を型として扱うことができる。

```dart
int calc(int a, int b) => a + b;
void exec(int Function(int, int) op) {
  print(op(2, 3));
}
exec(calc); // 5
```

### メタデータ

Dart ではアノテーション（メタデータ）を `@` 記号で付与できる。主にライブラリやツール向けの情報付加に使う。

```dart
@deprecated
void oldFunction() {
  // 非推奨の関数
}

@override
String toString() => 'MyClass';
```

### ライブラリのインポート

外部ライブラリやファイルを `import` 文で読み込む。

```dart
import 'dart:math';
import 'package:flutter/material.dart';
import 'my_utils.dart' as utils;
```

- `as` でプレフィックス指定
- `show`/`hide` で特定の識別子のみインポート/除外

```dart
import 'dart:math' show pi, sqrt;
import 'dart:math' hide Random;
```

### クラス

Dart ではクラスベースのオブジェクト指向がサポートされている。

```dart
class Point {
  int x;
  int y;

  // コンストラクター
  Point(this.x, this.y);

  // メソッド
  void move(int dx, int dy) {
    x += dx;
    y += dy;
  }
}
```

#### コンストラクター

- 通常コンストラクター
- 名前付きコンストラクター
- 初期化リスト
- ファクトリーコンストラクター

```dart
class Person {
  String name;
  int age;

  // 通常コンストラクター
  Person(this.name, this.age);

  // 名前付きコンストラクター
  Person.guest() : name = 'ゲスト', age = 0;

  // 初期化リスト
  Person.withBirth(String name, int birthYear)
      : name = name,
        age = DateTime.now().year - birthYear;

  // ファクトリーコンストラクター
  factory Person.fromJson(Map<String, dynamic> json) {
    return Person(json['name'], json['age']);
  }
}
```

#### メソッド

クラス内で定義する関数をメソッドと呼ぶ。`static` を付けるとクラスメソッドになる。

```dart
class Calculator {
  int add(int a, int b) => a + b;

  static int multiply(int a, int b) => a * b;
}
```

#### 継承

Dart ではクラスの継承がサポートされている。`extends` キーワードで親クラスを指定する。

```dart
class Animal {
  void eat() {
    print('食事中');
  }
}

class Dog extends Animal {
  void bark() {
    print('ワンワン');
  }
}

var dog = Dog();
dog.eat(); // 親クラスのメソッド
dog.bark(); // 子クラスのメソッド
```

#### Mixins

Mixin を使うと、複数のクラスから機能を継承できる。`with` キーワードを使う。

```dart
class Flyer {
  void fly() {
    print('飛んでいます');
  }
}

class Swimmer {
  void swim() {
    print('泳いでいます');
  }
}

class Duck with Flyer, Swimmer {
  void quack() {
    print('ガーガー');
  }
}

var duck = Duck();
duck.fly();
duck.swim();
duck.quack();
```

#### 列挙体

列挙型は、関連する定数の集合を表す。`enum` キーワードで定義する。

```dart
enum Color {
  red,
  green,
  blue
}

var c = Color.green;
```

#### 拡張メソッド

拡張メソッドを使うと、既存のクラスに新しいメソッドを追加できる。`extension`キーワードで定義する。

```dart
extension StringExtension on String {
  String hello() => 'Hello, $this!';
}

var s = 'Dart';
print(s.hello()); // Hello, Dart!
```

#### `extension type`

`extension type`は、既存の型に新しい型として振る舞いを追加できる（Dart 3以降）。

```dart
extension type UserId(int value) {
  int get id => value;
  String toHex() => value.toRadixString(16);
}

var uid = UserId(42);
print(uid.id);      // 42
print(uid.toHex()); // 2a
```

#### 呼び出し可能なオブジェクト

クラスに`call`メソッドを定義すると、インスタンスを関数のように呼び出せる。

```dart
class Adder {
  int call(int a, int b) => a + b;
}

var add = Adder();
print(add(2, 3)); // 5
```

### クラス修飾子

Dart 3以降では、クラスの継承やインスタンス化の制約を修飾子で指定できる。

- `abstract`：抽象クラス（直接インスタンス化できない）
- `base`：継承はできるが、`base`/`final`/`sealed`クラスからのみ継承可能
- `interface`：インターフェースとしてのみ実装可能
- `final`：継承不可
- `sealed`：同じライブラリ内でのみ継承可能

```dart
abstract class Animal {
  void speak();
}

base class BaseClass {}

interface class MyInterface {
  void foo();
}

final class FinalClass {}

sealed class SealedClass {}
```

### 並行プログラミング

Dart では、非同期処理やアイソレーション（Isolate）を使って並行プログラミングができる。

#### 非同期プログラミング

`Future`や`async`/`await`を使うことで、非同期処理を簡単に記述できる。

```dart
Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 1));
  return 'データ取得完了';
}

void main() async {
  print('取得開始');
  var result = await fetchData();
  print(result);
}
```

#### アイソレーション

Dart では、`Isolate`を使ってメインスレッドとは独立した並行処理ができる。Isolate間はメッセージで通信する。

```dart
import 'dart:isolate';

void sayHello(SendPort sendPort) {
  sendPort.send('Hello from Isolate!');
}

void main() async {
  var receivePort = ReceivePort();
  await Isolate.spawn(sayHello, receivePort.sendPort);
  print(await receivePort.first); // Hello from Isolate!
}
```

### null 安全

Dart は null 安全（null safety）をサポートしており、null 許容型と非許容型を区別できる。null 安全により、null 参照によるエラーを防げる。

```dart
String? name; // nullを許容
name = null; // OK

String message = 'Hello';
// message = null; // エラー（非許容型にはnullを代入できない）
```

### 予約語

Dart には、言語仕様で予約されているキーワードがある。これらは変数名や関数名などに使えない。

```
abstract  else      import    super
as        enum      in        switch
assert    export    interface  sync
async     extends   is        this
await     extension late      throw
break     external  library   true
case      factory   mixin     try
catch     false     new       typedef
class     final     null      var
const     finally   on        void
continue  for       operator  while
covariant Function  part      with
default   get       required  yield
do        hide      rethrow
```

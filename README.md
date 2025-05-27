# flutter-docs-md

## Flutter とは

**Flutter** (フラッター)は、Google によって開発された、フリーかつオープンなマルチプラットフォーム開発フレームワークである。全く同じコードで、Android / iOS / Web / Windows/ macOS / Linux といった、さまざまなプラットフォーム向けアプリケーションを開発することができる。
Flutter の開発言語には**Dart**が採用されている。

## Dart 入門

**Dart** (ダート/ダーツ)は、Google によって開発されたコンパイル型言語である。静的型付け、C スタイル構文、マルチパラダイムが特徴であり、Flutter による Web / モバイルアプリ開発などに使用される。

## Flutter 入門

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

### 制御構文

#### ループ (`for`/`while`/`do while`/`break`/`continue`)

#### 分岐 (`if`/`if-case`/`switch`)

#### エラーハンドリング (`try`/`catch`/`throw`)

### 関数

### メタデータ

### ライブラリのインポート

### クラス

#### コンストラクター

#### メソッド

#### 継承

#### Mixins

#### 列挙体

#### 拡張メソッド

#### `extension type`

#### 呼び出し可能なオブジェクト

### クラス修飾子

### 並行プログラミング

#### 非同期プログラミング

#### アイソレーション

### null 安全

### 予約語

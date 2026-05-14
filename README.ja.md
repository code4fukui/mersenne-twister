# Mersenne Twister

[
![npm version](https://badge.fury.io/js/mersenne-twister.svg)
](https://badge.fury.io/js/mersenne-twister)

Mersenne Twister MT19937 擬似乱数生成器のJavaScript実装。

## 特徴

- 周期 2¹⁹⁹³⁷-1 の擬似乱数を生成。
- 数値または配列によるシード（種）の指定をサポートし、再現可能な乱数列を生成。
- 異なる範囲や解像度に対応する複数のメソッドを提供。
- Node.jsおよびブラウザ環境の両方で動作。

## インストール

```bash
npm install mersenne-twister
```

## 使い方

**CommonJS (Node.js)**

```javascript
const MersenneTwister = require('mersenne-twister');
const generator = new MersenneTwister();

// [0,1) の乱数を生成
const randomNumber = generator.random();
```

**ES Modules**

```javascript
import MersenneTwister from 'mersenne-twister';
const generator = new MersenneTwister();

// [0,1) の乱数を生成
const randomNumber = generator.random();
```

## シード設定

再現可能な乱数列を生成するために、ジェネレータにシードを指定できます。シードが指定されない場合、ジェネレータは現在のタイムスタンプをシードとして初期化されます。

### 数値によるシード

コンストラクタまたは `init_seed` メソッドに整数を渡します。

```javascript
// インスタンス生成時にシードを設定
const generator = new MersenneTwister(123);

// または既存のインスタンスにシードを設定
generator.init_seed(456);
```

同じシードで初期化されたジェネレータは、完全に同じ数列を生成します。

### 配列によるシード

ジェネレータは数値の配列を使ってシードを設定することもできます。この方法は、Pythonの `random` モジュールなど、他の実装のシード設定の挙動と互換性があります。

```javascript
const seedArray = [0, 42, 1337];
const generator = new MersenneTwister(seedArray);
```

## APIメソッド

`MersenneTwister` インスタンスは以下のメソッドを持ちます：

- `random()`: 区間 `[0, 1)` の浮動小数点乱数を返します。これは最も一般的なメソッドであり、`Math.random()` と同等です。
- `random_int()`: 区間 `[0, 4294967295]` の32ビット整数乱数を返します。
- `random_incl()`: 区間 `[0, 1]` の浮動小数点乱数を返します（1.0を含む）。
- `random_excl()`: 区間 `(0, 1)` の浮動小数点乱数を返します（0.0と1.0を含まない）。
- `random_long()`: より高い精度を得るため、53ビットの解像度を持つ区間 `[0, 1)` の浮動小数点乱数を返します。
- `random_int31()`: 区間 `[0, 2147483647]` の31ビット整数乱数を返します。

## クレジット

このコードは、Makoto Matsumoto と Takuji Nishimura による MT19937 のオリジナルCプログラムを基にしています。JavaScriptへの移植版は、Sean McCullough によって最初に作成されました。

## ライセンス

MIT License — [LICENSE](LICENSE) を参照。

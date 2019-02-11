<style type="text/css">
<!--
.reveal h2 {
    text-transform: none;
    font-size: 42px;
}
.reveal p { font-size: 30px; }
.reveal ul li { font-size: 30px; }
-->
</style>

## TypeScript TDD トレーニング 02

変数と制御構文

[TDDトレーニング 目次](https://github.com/ababup1192/ts-tdd-document/blob/master/README.md)

---

## 目次

- 今日のポイント
- 変数とスコープ
- 制御構文
    - if-else
        - 条件演算子(三項演算子)
    - switch-case
    - while
    - for
- クイックTDD
- まとめ

---

## 今日のポイント

- 変数とスコープを理解すること
- 制御構文をTDDを通して学ぶこと

---

## 変数とスコープ

`let`と`const`と言うキーワードを使うことで変数を宣言し、そこに割り当られた値を参照することができる。letは再代入(再割り当て)可能であるが、constは再代入不可能な点で異なる。思わぬ値の変更による事故を防ぐために基本的にconstの利用が推奨される。

```javascript
> let x = 1
> let y = 2
> x + y
3
> x = 10
10
> x + y
12
> const z = 3
> x + y + z
15
> z = -1
TypeError: Assignment to constant variable.
```

---

## 変数とスコープ

変数名の後には、`:`の後に型注釈を付けることができる。一般的にリテラル(直接書くことができる基本型等の値)が右辺の場合には値から型が分かるため型注釈を省略することが多い。また関数も変数に代入することが可能である。

```typescript
> const n: number = 1;
> const str: string = true;
Type 'true' is not assignable to type 'string'.

> const f = (x: number) => x + 2;  
> const n2: number = f(5)
> n2
7
```

---

## 変数とスコープ

変数の生存期間を**スコープ**と呼ぶ。JavaScriptでは、波括弧で囲まれたブロックが基本的に変数のスコープとなる。

```typescript
// xは、このブロックがスコープとなる。
> { const x = 10; console.log(x * 2); } 
20
// スコープ外からは参照出来ない。
> console.log(x)
ReferenceError: x is not defined
> const f = () => { 
    let y = 1;
    // yは関数ブロックがスコープの為、中のブロックもスコープに含まれ、値の更新もできる。 
    { console.log(y); y = 2; } 
    console.log(y); 
  }
> f()
1
2
```
---

## 制御構文 if-else

if-elseは条件式(boolean型)を利用することで分岐を表す制御構文です。

```typescript
> if(true) { console.log('true';) } else { console.log('false'); }
true
> const x = 50;
> if(x < 50) { console.log('x < 50'); } else { console.log('x >= 50') }
x >= 50
// 結果を一時変数(temporary)に代入して、あとで計算する
> let tmp;
// elseにif-elseを繋げることで複数の条件を繋げることができる
> if(x === 100) { tmp = x; } else if(x < 50) { tmp = x / 2; } else { tmp = x * 2;  }
> tmp * 2
200
```
---

## 条件演算子(三項演算子)

if-elseは文のため値を返しません。式は値を返します。条件演算子は条件に応じて値を返す式です。

```typescript
> const x = 50;
> let tmp;
// ２つは等価です。
> if(x < 100) { tmp = x * 2; } else { tmp = x / 2; }
> tmp * 2
200

> const result = x < 100 ? x * 2 : x / 2; 
> result * 2
200
// 更に一時変数を減らせる。
> (x < 100 ? x * 2 : x / 2) * 2;
200
```

---

## クイックTDD

- 

---

## まとめ

- 

---

## 参考文献

- [TypeScript (Variable Declarations)](http://www.typescriptlang.org/docs/handbook/variable-declarations.html)
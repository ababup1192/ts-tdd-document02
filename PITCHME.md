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

## クイックTDD

- 男('man')か？
- 年齢が大人(18歳以上)かどうか？
- ２つの数字の和
- ２つの文字列を繋げる
- '私は次の誕生日で、12歳です。'
- ２つの数字の商
- 文字列の長さ
- 頭と末尾の文字を削る

---

## まとめ

- 

---

## 参考文献

- [TypeScript (Variable Declarations)](http://www.typescriptlang.org/docs/handbook/variable-declarations.html)
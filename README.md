# Hacker-site

セキュリティ好きの自己紹介サイトです。静的ファイルだけで動きます（HTML / CSS / JavaScript）。

## 中身

- `index.html` … 自己紹介ページ本体
- `style.css` … スタイル（ターミナル風のダークテーマ）

## ⚠️ 意図的な脆弱性（学習用）

このサイトには **DOM-based XSS** の脆弱性が1つ、学習目的で意図的に入っています。

- **場所**: `index.html` の `greet()` 関数
- **原因**: URLの `?name=` の値を検証せずに `innerHTML` へ代入している
- **試し方**: `index.html?name=<img src=x onerror=alert(document.domain)>` をブラウザで開く
- **修正方法**: `innerHTML` の代わりに `textContent` を使う

```js
// 修正前（脆弱）
document.getElementById("greeting").innerHTML = "ようこそ、" + name + " さん！";

// 修正後（安全）
document.getElementById("greeting").textContent = "ようこそ、" + name + " さん！";
```

> 公開運用する場合は、上の修正を適用してください。この脆弱性は自分で攻撃の仕組みを確かめるための教材です。

## 使い方

ブラウザで `index.html` を開くだけで見られます。GitHub Pages などで公開する場合は、`index.html` の名前・連絡先を自分の情報に書き換えてください。

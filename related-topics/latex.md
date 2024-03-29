---
description: Latexについて
---

# LaTex

$$\LaTeX$$とは$$\TeX$$という組版システムを下敷きにした**マクロ体系**のことです

｢なんのこっちゃ｣と思った方もいると思いますが気になる方以外は数式が便利に使えるツールだというくらいの理解度で大丈夫です

$$\LaTeX$$が使われる場面は主にレポートを想定しています

### 基本

#### インライン表記

`$数式$` もしくは`\(数式\)` のように書くとインライン表記ができます

インライン表記とは$$1+1=2$$こんな感じに文章中に数式を書くことです

#### ディスプレイ表記

`$$数式$$` もしくは `\[数式\]` のように書くとディスプレイ表記ができます

こんな感じです

$$
1+1 = 2
$$

ただ,`$$` で囲むやり方は正確には$$\TeX$$のコマンドであり$$\LaTeX$$で使うべきではありません

ただ,ウェブ上で$$\LaTeX$$で記述された数式を表示するMathJaxというライブラリではよく使われ,逆に後者の方が使われていなかったりするので割り切って使う必要もあります

{% hint style="info" %}
本文が書かれているGitbookもMathJaxによって数式が表現されています
{% endhint %}

### 環境

手元のエディタで$$\LaTeX$$を書くというのも可能ですが,環境構築が面倒です

手軽に始められるためここでは[Overleaf](https://ja.overleaf.com/)というオンラインエディタをおすすめします

Overleafではオンライン上でドキュメントを管理し書くことが可能です

まずはアカウントの登録をします.登録が済んだら,次は空のプロジェクトを立ち上げます

プロジェクトを立ち上げるとそのプロジェクトにあるファイルを用いて文書を作成することが可能です

プロジェクトを開くと以下のようになっていると思います

![&#x65E5;&#x672C;&#x8A9E;&#x304C;&#x8A2D;&#x5B9A;&#x8A00;&#x8A9E;&#x3060;&#x3068;&#x3053;&#x306E;&#x3088;&#x3046;&#x306A;&#x753B;&#x9762;&#x306B;&#x306A;&#x308A;&#x307E;&#x3059;](../.gitbook/assets/image%20%281%29.png)

ここで左上にある｢メニュー｣を選び｢コンパイラ｣を｢LaTeX｣に変更します

![&#x30B3;&#x30F3;&#x30D1;&#x30A4;&#x30E9;&#x304C;LaTex&#x306B;&#x5909;&#x66F4;&#x3055;&#x308C;&#x3066;&#x3044;&#x307E;&#x3059;](../.gitbook/assets/image%20%282%29.png)

また｢メニュー｣の下にあるロゴのうち,最も左のものを選択肢し新規ファイルを作ります

![&#x3053;&#x308C;&#x306E;&#x4E00;&#x756A;&#x5DE6;&#x3067;&#x3059;](../.gitbook/assets/image%20%283%29.png)

ファイル名を`latexmkrc` に変更します

![&#x65B0;&#x3057;&#x3044;&#x30D5;&#x30A1;&#x30A4;&#x30EB;&#x306F;&#x30C7;&#x30D5;&#x30A9;&#x30EB;&#x30C8;&#x3060;&#x3068;&quot;name.tex&quot;&#x3068;&#x3044;&#x3046;&#x540D;&#x524D;&#x3067;&#x3059;&#x304C;&quot;.tex&quot;&#x3082;&#x6D88;&#x3057;&#x3066;&#x69CB;&#x3044;&#x307E;&#x305B;&#x3093;](../.gitbook/assets/image%20%284%29.png)

その後,`latexmkrc` に以下のように書き込みます

```text
$latex = 'platex';
$bibtex = 'pbibtex';
$dvipdf = 'dvipdfmx %O -o %D %S';
$makeindex = 'mendex %O -o %D %S';
$pdf_mode = 3; 
```

このようなファイルを作ることでOverleafで日本語が使えるようになります

あとは必要に応じてPackageを入れればレポートなどの作成を非常に楽にすることができます

![&#x65E5;&#x672C;&#x8A9E;&#x304C;&#x66F8;&#x304D;&#x8FBC;&#x3081;&#x308B;&#x3088;&#x3046;&#x306B;&#x306A;&#x308A;&#x307E;&#x3057;&#x305F;](../.gitbook/assets/image%20%285%29.png)

### 数式

### 全体


---
description: エディタについて
---

# Editor

エディタとは文字通り文書をedit\(編集\)するものです

しかしただ文字を入力するだけというのも不便です

そのためプログラミングをするためには様々な高性能のエディタが開発されています

{% hint style="info" %}
今後

```text
$ mkdir prog
$ cd prog
```

のような記述をしますが,`$` は実際には入力しないでください

`$`は｢この操作がTerminal内のものですよ｣ということを表しています
{% endhint %}

### Visual Studio Code

プログラミングを始めたばかりという人におすすめのエディタです

軽くて最低限必要な機能が充実しており初心者におすすめです

また拡張機能をあとから追加することも可能で長く使えそうな点も良いです

Ubuntuを利用している方は以下のコマンドをTerminalに入力してください

```text
$ sudo apt-get install apt-transport-https
$ sudo apt-get update
$ sudo apt-get install code # or code-insiders
```

Mac OSを利用している方は以下のHomebrewをインストールしていない方は

```text
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

をTerminalに入力してインストールを済ませてください

HomebrewとはMac OSのパッケージ管理ソフトウェアです

つまり,ソフトウェアを管理するソフトウェアです

{% hint style="info" %}
`もちろんこのソフトウェアは非常に人気で多くのエンジニアが使っていますが...`

`Homebrewを作ったエンジニアは`[`Googleの面接で二分木を反転させることができずに落とされました`](https://twitter.com/mxcl/status/608682016205344768?s=20)\`\`
{% endhint %}

その後,

```text
$ brew　update
$ brew cask install visual-studio-code
```

と入力することでMac OSにインストールは完了します


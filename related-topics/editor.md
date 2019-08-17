---
description: エディタについて
---

# Editor

エディタとは文字通り文書をedit\(編集\)するものです

しかしただ文字を入力するだけというのも不便です.文字をご入力した際に困るということは想像するに容易いでしょう

そのためプログラミングをするためには様々な高性能のエディタが開発されています

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



## Emacs

Emacsとはエディタというよりもはや一つの環境です

ブラウザ･メール･ゲームなどほとんどなんでもできるという非常に強い拡張性を持っています

### インストール

Mac OSの場合は

```text
brew install emacs # Terminal上で開きます
brew install emacs --with-cocoa # 普通のアプリケーションと同様に開きます
brew cask install emacs # 上に加えてLaunchpadにアプリケーションが追加されます
```

下2つは通常のアプリケーションと同じように開けますが

```text
$ emacs -nw
```

と起動するとTerminalのwindow上で開くことができます

Ubuntuの場合は以下のようにします

```text
$ sudo apt install emacs
```

### 共通

```text
$ emacs
```

で起動させます

* Controlキーを`C`，Metaキー\(基本的にはOption，alt\)を`M`とする
* Emacs終了:`C-x C-c`
* 動作の戻り/進み
  * Emacsの動作の取り消し:`C-g`
  * Undo:`C-/`

### 移動

* 一文字分
  * 上:`C-p`下:`C-n`右:`C-b`左:`C-f`
* 上下:ページごとの移動，左右:文字ごとの移動
  * 上:`M-v`下:`C-v`右:`M-b`左:`M-f`
* 行ごとの移動
  * 右:`C-a`左:`C-e`
* 現在のカーソルを中心に:`C-l`

### 文字列

* 検索
  * 次の文字列:`C-s`
  * 前の文字列:`C-r`
* 置換
  * `M-x replace-string`
* 削除・範囲指定・コピー・ペースト
  * 全選択:`C-x h`
  * 行末まで削除:`C-k`
  * 範囲指定:`C-@`
  * コピー:`M-w`
  * 貼り付け:`C-y`
    * `M-y`: コピーする内容を遡る
* 行の連結:`M-^`

### ウィンドウ

* 移動: `C-x o`
* 現在のウィンドウを閉じる: `C-x 0`
* 現在のウィンドウ以外を閉じる: `C-x 1`
* ウィンドウを上下に分割する: `C-x 2`
* ウィンドウを左右に分割する: `C-x 3`

### バッファ

* バッファ呼び出し: `C-x C-b`
  * バッファ消去マーク:`d`
  * 実行:`x`
* `.emacs`などの読み込み: `M-x eval-buffer`

### ファイルの実行

* コンパイル:`M-x compil`を入力後，`gcc sample.c`など
* 実行:`M-x shel`

### エラーに関して

* packagesをインストールするときに`Not found`が出てくる: `M-x package-refresh-contents`

### ファイル管理

* ディレクトリ
  * ディレクトリ作成: `M-x make-directory RET <ディレクトリ名> RET`
* ファイル
  * `C-x C-f`: ファイルを検索\(ない場合は新たに作成\)
  * `C-x C-s`: ファイルをセーブ

### `package`の管理

* 初期化ファイルはの以下の順番で優先され，一つしか読み込まれないので注意
  1. `.emacs`
  2. `.emacs.el`
  3. `emacs.d/init.el`
* `.emacs`と`.emacs.el`ではホームディレクトリ直下に他の`.el`ファイルが散乱するので，`init.el`にするのが無難
* packageのリストを開く:`M-x package-list-packages`
  * すべての`package`をupgrade:開いた状態で`U`を`Upgrade`マークをつけて，`x`で実行する
  * インストール:`C-s`で検索モードにするか，移動して`package`を見つける．`i`で`install`マークをつけて，`x`で実行
  * meplaなどに繋がらないとき:`package-refresh-contents`

### Magitの使い方

Emacsの拡張機能です

Gitの機能を使うことができます

* `git init` : `M-x magit-init`
* 以下は`M-x magit-status`を押してからする．これがこのコマンドが起点となって色々する．
  * `git add`
    * `Untracked files`にカーソルを合わせて`s`を押すことで，`stage`
    * `S`ですべてのファイルを`stage`
    * `u`で`unstage`
    * `U`ですべてのファイルを`unstage`
    * `M a`:`git remote add`
  * `git commit`
    * `c`:`commit mode`に変更
    * `c`を押すと`staged`なものを`commit`できる
    * `commit message`を入力して`C-c C-c`を入力して`commit`完了
  * `git log`
    * `l`:`commit mode`に変更
    * `b`:ログを見られる
  * `git branch`
    * `b`:`branch mode`に変更
    * `c`:`new branch`に`checkout`
    * `b`:`master`に`checkout`
    * `m`:`merge`
  * `git push`
    * `P`:`push mode`に変更
    * `p`:`push`
    * `u`:`upstream`を指定してpush`先を選ぶ(`push`先を指定しないとここに`push\`される\)
  * `git fetch`
    * `f`:`fetch mode`に変更
    * `a`:`fetch`をすべてのリモートリポジトリからする
  * `git pull`
    * `F`:`pull mode`に変更
    * `u`:`origin/master`から`pull`

### neotree

Emacsの拡張機能です

サイドバーにファイルやディレクトリを表示することができます

* 上下移動:`p`&`n`
* 開く: `SPC`/`RET`/`TAB`
* 一つ上のディレクトリへ:`U`
* 再読込:`g`
* 最大化/最小化:`A`
* 隠しファイルの表示/非表示:`H`
* 下のディレクトリをすべて開く:`O`
* 新しいディレクトリ/ファイルを作る\(`/`で終わるときはディレクトリ\): `C-c C-n`
* ディレクトリ/ファイルを削除:`C-c C-d`
* ディレクトリ/ファイルの名前を変更:`C-c C-r`
* ルートディレクトリを変更する:`C-c C-c`
* ディレクトリ/ファイルをコピーする:`C-c C-p`

### iTerm2

これはエディタではないですが,どこに書くか迷った結果ここに書くことになりました

iTerm2はTerminalアプリでMac OSを使っている方は以下のコマンドでダウンロードをすることが可能です

```text
$ brew cask install iterm2
```

* 初期化:`defaults delete com.googlecode.iterm2`
* 諸設定:[https://qiita.com/ruwatana/items/8d9c174250061721ad11](https://qiita.com/ruwatana/items/8d9c174250061721ad11)


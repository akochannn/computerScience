---
description: Gitについて
---

# Git

プログラムの変更履歴を記録する**分散型バージョン管理システム**のことです

Gitを使うことで間違えて書いたソースコードを戻すことができ,また複数のバージョンを同時に管理することで複数人でプログラムを編集することができます

{% hint style="info" %}
### ちなみに

Gitのメンテナンスをしているのは**濱野純**という日本出身の方です  
現在はカリフォルニアに在住してますが日本人がOSSをしているのを知らなくて調べていて編集者がびっくりしたという話です
{% endhint %}

### 使い方

大まかには以下のように使います

まずはGIt管理をしたいディレクトリ\(フォルダのことです\)上に行きます

```text
$ git init # Git管理を始める
```

以上のコマンドでそのディレクトリのGit管理を始めることが可能です

この際にこのディレクトリのことを**レポジトリ\(repository\)**と言います

#### 作業の流れ

ところでGitでは履歴の流れを分岐して記憶しています

このそれぞれの分岐を**ブランチ\(branch\)**と言います

この分岐をまとめることを**マージ\(merge\)**と言い,ソフトウェアには重要です

ブランチを分岐させるにはそのブランチ\(枝\)が一本もない状態では無理です

最初のブランチは最初に履歴を記録した時にできます.このブランチを**masterブランチ**と言います

記録をする手順は以下の通りです

```text
$ git add . # レポジトリ内のファイルを全てステージする
$ git commit -m "message" #  メッセージと一緒にコミットする
```

**ステージ\(stage\)**とは次のコミットをするファイルを定める場所,**インデックス\(index\)**にファイルを含めるということです

上のように`$ git add` をしてどのファイルをステージするか決めます.`.`か`-A`で全てのファイルをステージすると定めます.下のように直接ファイル名を書いて指定することも可能です

```text
$ git add [filename] # filenameというファイルをステージする
```

**コミット\(commit\)**はステージされたファイルの差分を記録することです

このようにブランチに差分を記録していきます.また

**ブランチを切る**\(奇妙な表現ですがブランチを作るということです\)ことで変更する部分ごとに同時並行でソフトウェアを管理します

```text
$ git checkout -b newBranch # newBranchという新しいブランチを作り,そのブランチに移ります
$ git branch newBranch # newBranchという新しいブランチを作るだけで,そのブランチには移りません
```

新しいブランチを上のように作っていきます

今いるブランチを確認するには下のコマンドが有効です

```text
$ git branch # 現在あるブランチ･今いるブランチを表示
```

このようにして分岐した変更点をまとめることを**マージ\(merge\)**と言います

ここではmasterブランチから始まったと仮定して,testブランチを切り編集したファイルをmasterにマージする手順を実際に見てみます

```text
$ git branch # 現在あるブランチと自分のいるブランチ(master)を確認する
$ git checkout -b test # testブランチに移る
$ emacs test.c # test.cというファイルを編集したとします
$ git checkout master # masterブランチに戻る
$ git merge test # masterブランチにtestブランチをマージさせる
```

このようなやり取りを繰り返すことでファイルを編集していきます


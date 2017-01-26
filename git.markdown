# Git

* 作業ディレクトリ
* ステージングエリア（インデックス）
* リポジトリ（ローカル、リモート）

## 名前とメールの設定
* git config --global user.name "naoki"
* git config --global user.email "naoki@gmail.com"
* git config -l

## リポジトリの作成
1. midir prj
2. cd prj
3. git init

## ファイルをコミット
4. cat "test" > file
5. git add file ※ステージングエリアに追加
6. git commit
7. git log --oneline

## 状態を確認する
1. git status

## 差分を確認する
* 作業ディレクトリとステージングエリアの差分を表示
  * git diff
* ステージングエリアとリポジトリの差分を表示
  * git diff cached

## ファイルの変更を取り消す
1. cat "test" > file
2. git checkout -- file

## 通常の流れ
1. mkdir prj
2. cd prj
3. git init
4. cat "test" > file
5. git diff
6. git add file
7. git diff cached
8. git log

## コミット履歴を指定して変更を戻す
* git reset --hard HEAD ※ステージングエリア、作業ディレクトリを最新コミットに戻す
* git reset --hard HEAD^ ※リポジトリ、ステージングエリア、作業ディレクトリをひとつ前のコミットに戻す
* git reset HEAD^ ※リポジトリ、ステージングエリアをひとつ前のコミットに戻す

* 補足（http://qiita.com/shuntaro_tamura/items/db1aef9cf9d78db50ffe）
  * reset --hard：全部Yに戻す。
  * reset --mixed(何もなし）：commitとaddの取り消し。
  * reset --soft：commitのみ取り消し。

## gitで管理しないファイルを*.gitignore*ファイルに書いておく
~~~
*.log
~~~

## ブランチ
* ブランチ作成
  * git branch hoge
* ブランチリストの確認
  * git branch
* 操作しているブランチの切り替え
  * git checkout hoge
* ブランチの削除
  * giy branch -d hoge

## マージ
1. git branch master
2. git merge hoge ※衝突が起こった場合、ファイルを開いてどちらかの行を消す

## タグ
コミットIDに別名をつける機能
* 直前のコミットにタグをつける
  * git tag v1.1
* タグの確認
  * git tag
* IDを指定してタグをつける
  * git tag v1.2 b813245
* タグの削除
  * git tag -d v1.2

## エイリアス
* git config --global alias.co checkout
  * co = checkout

## 共有リポジトリを介してデータを共有
### 共有ディレクトリを作成
1. mkdir ourweb.git
2. cd ourweb.git
3. git init --bare

### Aさんが共有リポジトリにＰＵＳＨ
1. git remote add origin ~/ourweb.git ※共有リポジトリを登録
2. git config -l
3. git push origin master ※共有リポジトリ(origin)にmasterの内容を追加

### Bさんが共有リポジトリをCLONE
1. git clone ~/ourweb.git/ myweb2
2. cd myweb2
3. git log

### 共有リポジトリとローカルリポジトリで衝突が起こった場合
1. git push origin master ※衝突
2. git pull origin master ※共有リポジトリを取得してローカルで衝突を解決
3. ファイルを修正
4. git commit -am "conflict fixed"
5. git push origin master

## 便利
* git add . カレントディレクトリ以下すべてのファイルをadd
* git rm file
* git mv file file2
* git commit --amend ※直前のコミットに変更を反映させる
* git checkout -b hoge ※ブランチ作成と切り替えを一気に行う
* git commit -am ”メッセージ” ※addとcommitを一気に
* git show v1.2
* git remote rm origin ※リポートリポジトリの登録を削除

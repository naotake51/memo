# GitHub

## GitHubとは
Gitのリモートリポジトリを提供してくれるサービス

## GitHub構築手順
1. GitHubにアカウント作成
2. GitHubにリモートリポジトリ作成
3. GitHubにSSH接続できるようにする
4. ローカルリポジトリを作成してリモートリポジトリにpush

## GitHubにアカウント作成
https://github.com/

# GitHubにリモートリポジトリ作成
https://github.com/

# GitHubにSSH接続できるようにする
1. cd ~/.ssh ※SSH通信に必要ないろいろを保存する一般的な場所
2. ssh-keygen -t rsa
  * id_rsa(秘密鍵)とid_rsa.pub(公開鍵)を作成する
  * パズワードの設定などを聞かれるがとりあえず、Returnを3回でOK
3. `chmod 600 id rsa`
4. id_rsa.pubをGitHubに登録
  1. (https://github.com/settings/keys)にアクセスして'New SSH key'を押す
  2. Title は適当にid_rsa.pub for vagrantとでもしておく
  3. Keyはid_rsa.pubの内容をコピペ
  4. Add SSH keyを押す

# ローカルリポジトリを作成してリモートリポジトリにpush
GitHubページに書いているのを参考におこなえばよい
> echo "# memo" >> README.md  
> git init  
> git add README.md  
> git commit -m "first commit"  
> git remote add origin git@github.com:naotake51/memo.git  
> git push -u origin master  ※最初の一回は"なりすまし防止"のため、公開鍵がホストのものか確認を要求される

# SSH

## OpenSSH
SSH通信を行うためのデファクトスタンダードプログラム

## ユーザーがログインするまでの流れ
1. ホスト認証
2. ユーザー認証

## ホスト認証
1. ホストの公開鍵を取得
2. 公開鍵がホストのものであることをユーザーに確認
  * 認めたら、ホストと公開鍵のペアは~/.ssh/known_hostsに登録され2回目以降確認不要になる
3. ユーザーは、公開鍵で乱数を暗号化してホストに送る。ホストは乱数を当てることで自分が公開鍵に対応する秘密鍵を所持していることを証明する

## ユーザー認証(公開鍵認証)
1. ユーザーの公開鍵をホストに登録 ※~/.ssh/authorized_keys に登録される
2. ホストは、公開鍵で乱数を暗号化してユーザーに送る。ユーザーは乱数を当てることで自分が公開鍵に対応する秘密鍵を所持していることを証明する

## SSH通信をする手順(まだ実際に行っていない)
1. サーバー側に公開鍵の保存場所を作る
  1. `mkdir ~/.ssh`
  2. `chmode 700 ~/.ssh`
2. リモート側で公開鍵、秘密鍵を作成
  1. `ssh-keygen -t rsa -v`
  2. 鍵の名前を聞かれるがデフォルトでいいのでReternでOK
  3. 秘密鍵id_rsa、公開鍵id_rsa.pubができていることを確認
  4. `chmod 600 ~/.ssh/id_rsa.pub`
3. 公開鍵をサーバーに転送
  1. `scp ~/.ssh/id_rsa.pub username@url:~/ssh/autohorized_keys`
  2. OKですかと聞かれるのでYES
  3. paswordを聞かれるので入力
4. 秘密鍵をつかってサーバーにログイン
  1. `ssh -i ~/.ssh/id_rsa username@url`
    * デフォルトで~/.sshを参照するので `ssh usrname@url`でもOK

http://dotinstall.com/lessons/basic_sakura_vps/8008

## 参考
http://www.unixuser.org/~euske/doc/openssh/book/chap3.html

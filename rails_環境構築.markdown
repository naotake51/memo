# railsアプリ開発環境構築手順

0. VirturlBoxをインストール

0. Vagrantをインストール

0. Cywinをインストール
  - ※SSHモジュールを追加しておく

0. SVNインストール

0. cygwin/home/naokiの配下に作業ディレクトリ作成

0. 作業ディレクトリをSVNで管理する

0. vagrant `add centos6.5 http://...`でbaseboxを取得

0. 作業ディレクトリで `vagrant init centos6.5`でVagrantfileを作成

0. virturl box のポートフォアリング機能でゲストの3000とホストの3000を結びつける
  - Vagrantfileに `config.vm.network "forwarded_port", guest: 3000, host: 3000`を書くことで、プロファイル時に自動で行ってくれる

0. `vagrant up`でホストマシン起動

0. `vagrant ssh`でホストに乗り込む

0. rvmをインストール
  1. `curl -sSL https://get.rvm.io | bash`を実行（https://get.rvm.ioのスクリプトを実行）
  1. `~/.profile`を実行（環境変数パスを通したり）

0. rubyをインストール
  1. `rvm list known`でダウンロード可能なrubyバージョンを調べる
  1. `rvm install 2.3.1`でruby2.3.1をダウンロード

0. railsをインストール
  1. `gem install rails`railsをインストール

0. railsアプリを作成
  1. `rails new ディレクトリ名`でrailsアプリのひな型作成

0. gimを追加
  1. Gimefileの `# gem 'therubyracer', platforms: :ruby`のコメントアウトを外す。
    - ※このままrails sをすると"Bundler Error Backtrace:"がでた。どうやらtherubyracerが必要らいしい
  1. slim,sassでコーディングするなた以下のgemも追記
    2. `gem 'slim-rails'`
    2. `gem 'bootstrap-sass'`
    2. `bundle install`を実行してgemを追加

0. railsアプリを実行
  - `rails s -b 0.0.0.0`でサーバーアプリ実行(&をつけるとバックグラウンドで実行)
    - ※rails sではゲスト側からアクセスできなかった

## 問題
* 開発モードなのにrailsのコントローラーを変更しても反映されない問題が起こった
`config/environments/development.rb`の
`config.file_watcher = ActiveSupport::EventedFileUpdateChecker`を
`config.file_watcher = ActiveSupport::FileUpdateChecker`に
変更すると反映されるようになった。
https://www.tcmobile.jp/dev_blog/programming/rails5-on-vagrant-%E3%81%AEdevelopment%E3%81%A7%E3%82%B3%E3%83%BC%E3%83%89%E3%81%AE%E5%A4%89%E6%9B%B4%E3%81%8C%E5%8F%8D%E6%98%A0%E3%81%95%E3%82%8C%E3%81%AA%E3%81%84/

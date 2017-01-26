
# rails

＊ railsアプリケーション作成
  - `rails new [apprication name]`

＊ railsアプリを実行
  - `rails server(s)`
  - virtualbox環境では `rails s -b 0.0.0.0`

## Scaffold

＊ scaffoldでCURDの足場作成
  - rails g(generate) scaffold Group name:string description:text

＊ scaffoldで作成したファイルを全削除
  - rails d(destroy) scaffold name

＊ 参照関係を明示してScaffold
  - rails g scaffold User group:references name:string profile:text

* コントローラー作成
  - rails generate controller welcome index

＊ RailsのScaffoldのテンプレートをカスタマイズする
  - 多分、これがテンプレートファイルと思われる
  - cat /home/vagrant/.rvm/gems/ruby-2.3.1/gems/jbuilder-2.6.1/lib/generators/rails/templates/controller.rb
  - cat /home/vagrant/.rvm/gems/ruby-2.3.1/gems/jbuilder-2.6.0/lib/generators/rails/templates/controller.rb

## コントローラ作成

* コントローラーを作成
  - rails g controller articles ※データベースと連携して使う場合コントローラー名は複数形s

* コントローラーの削除
  - rails d controller articles index

## モデル操作

* モデルを作成
  - rails g model Article title:string text:text

* モデルを削除
  - rails d model Article

* カラム追加のマイグレーションファイルを作成。
  - rails g migration add_hyouka_to_items good:integer bad:integer

* カラム削除
  - rails g migration remove_hyouka_from_items good:integer bad:integer

* マイグレーションでDBに反映
  - rake db:migrate

* 1つ前のバージョンの状態に戻す
  - rake db:rollback

* バージョン指定してdownメソッドを行う
  - rake db:migrate:down VERSION=20161204134348

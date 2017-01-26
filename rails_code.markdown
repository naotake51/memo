# rails code

## routes.rb（ルートを管理するファイル)

* welcomeコントローラーのindexアクションへのルートを作成
  - <http://localhost:3000/welcome/index>でアクセス
  - `get 'welcome/index'`

* ホームのルートを作成
  - <http://localhost:3000>でwelcomeコントローラーのindexアクションへ
  - `root 'rankings#index'`

* articlesに関するCURD(create read update delete)のルートをすべて作成
  * `resources :articles`
  * 親子関係のあるモデルは
  ~~~
  resources :articles do
    resources :kodomio
  end
  ~~~

## other

* フォームの書き方
~~~
<%= form_for [モデルオブジェクト(:article)], url: [フォームの送信先] do |f| %>
  <%= f.text_field :title %><br>
  <%= f.text_area :text %><br>
  <%= f.submit %>
<% end %>
~~~


* 共通部分の抜き出し
~~~
_[name].html.erbファイルに共通部分を書き
<%= render @[name] %>で参照
~~~

* Debug
~~~
render plain: params[:item].inspect  params[:item]の中身を表示
raise param.inspect  例外を発生させてparamのすべてを表示
~~~

* リダイレクト
~~~
redirect_to items_path
~~~
* レンダー
~~~
render "edit"
~~~

* nomalize.cssを最初に読み込ませるためにapplicationcssファイルを変更
~~~
application
 *= require_self
 *= require normalize.css  →app/assets/normalize.cssを読み込む
 *= require_tree .       →app/assets/stylesheets以下の全CSSファイルを読み込む部分
~~~

## ActiveRecode

### モデル定義

* バリデーション
~~~
  Itemクラスに書く
  validates :title, presence:true
  validates :body, length: {minimum: 5}
~~~

* スコープ
~~~
  Itemクラスに書く
  scope :top3, order("created_at").limit(3)
  下記で使用できる
  Item.top3
~~~

* アソシエーション
~~~
  1対Ｎの関係
  class Post < ActiveRecord::Base
  has_many: comments, dependent: destroy
  end
  ※dependent: destroyは、postを削除したときに紐づいているcommentも一緒に消すオプション

  class Comment < ActiveRecord::Base
  belongs_to :post
  end
~~~

### 使用例

* データの基本操作
~~~
  @item = Item.find params[:id]
  @items = Item.all
  @item.destroy
  @item.update(parawms.repuire(:item).permit(:name))
  @item.new(params.require(:item).permit(:name))
  @item.save
~~~

* 値を指定してデータを取得する
~~~
  Item.find_by_title("title1")
  Item.find_by_title_and_id("title2", 1)
  Item.where(title:"title1", id:1)
  Item.where("title = ? and id = ?", "title1", 1)
  Item.where("id > ?", 2)
  Item.where("title like ?", "hello%")
  Item.where(id: 1..3)
  Item.where(id: [i,3])
~~~

* データをソートして取り出す
~~~
Item.order("id desc").limit(3)
~~~

* レコードのカラムを変更
~~~
  @item.update_attribute(:title, "newtitle")
  @item.update_attributes(title: "newtitle", body: "ffff")
  Item.where(id: [i,3]).update_all(title: "newtitle", body: "ffff")
~~~

* レコードの削除
~~~
  delete :レコードの削除  早い
    Item.where(id: 1..3).delete_all
    @item.delete

  destroy: 高機能（関連する子レコードを消したり）、  遅い
    Item.where(id: 1..3).destroy_all
    @item.destroy
~~~

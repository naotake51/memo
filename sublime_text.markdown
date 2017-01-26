# Sublime Text

## パッケージ

### まず最初に、パッケージコントロールを入れる（パッケージをインストールしたり管理するツール）
* PackageControl

### railsで使用するパッケージ
* "Ruby on Rails snippets" => Railsのハイライトとスニペット
* "Ruby Slim" => Slimのハイライトとスニペット
* "SCSS", "SCSS Snippets" => SCSSのハイライトとスニペット

### Markdownで便利なパッケージ
* Monokai Extended（マークダウンのシンタックスハイライト表示）
* Markdown Extended（挿入したコードのシンタックスハイライト表示）
* Trailing Space（半角スペースの可視化）
* OmniMarkup Previewer（リアルタイムプレビュー） ※Ctr + Alt + oでプレビュー
* Table Editor（表作成の簡易化）

## 設定
* Preferences→SettingでUserでDefaultの設定をオーバーライドできる
Keybindingsも同様

* Settingの
"ignored_packages":["Vintage"]を
"ignored_packages":[]に
変更するとvimと同じキーバインドになる

## ショートカット

### サイドバーのトグル
Ctrl + K → Ctrl + B

### コマンドパレットを開く
Ctr + Shift + P

### コメントのトグル
Ctr + / でコメントにできる

### 複数選択
  Ctr + d / Ctr + U
  Ctr + マウスドラグ

### ファイル検索

### 矩形選択
Ctr + Alt + ↑↓ ※Windowsのホットキーと競合しているのでホットキーを無効化する必要がある
#### ホットキー無効化の方法
http://www.starlod.net/sublime-text-3-shortcutkey.html
> 1. デスクトップのウィンドウの無いところで、マウスを右クリックする。
> 2. 表示されたメニューの中にある「グラフィック オプション」にカールを合わせる。
> 3. 表示されたサブメ888844ニューの中にある「ホットキー」にカーソルを合わせる。
> 4. 表示されたサブメニューの中から「無効」を選択する。

### 移動
#### ファイルへ
Ctr + P  
ファイル名をあいまいに入力する @[synbol]を付加することで、シンボルにとべる :[number]を付加することで、その行番号にとべる
#### シンボルへ
Ctr + R
#### 行番号へ
Ctr + G
#### 定義もとへ
* 宣言へ F12
* 呼び出し元へ Alt + -



### ウィンドウの操作
#### 分割
Alt + Shift + 2,3,4
#### 移動
Ctr + [ウィンドウ番号]

### 行の削除
Ctrl + Shift + K

## その他
### project editでサイドバーに表示するファイル群を選べる
    {
      "path": "ranking_app/app"
    },

### スニペット
.sublime-snippet
http://dotinstall.com/lessons/basic_sublimetext/10510

### Build機能
http://dotinstall.com/lessons/basic_sublimetext/10511


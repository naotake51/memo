# Atom

## 公式ページ
  https://atom.io/
### パッケージ作成のときに役立つリファレンス
  https://atom.io/docs/api/v1.14.4/AtomEnvironment


## 構築手順
1. プログラミングに適したフォントをインストール
  1. RictyDiminished-Regular.ttfをダウンロード
  (https://github.com/edihbrandon/RictyDiminished/blob/master/RictyDiminished-Regular.ttf)

  2. ttfファイルを開いてインストールを押す。
    * コントロール パネル\デスクトップのカスタマイズ\フォント に RictyDiminished があることを確認

2. Atomの設定
  * SettingsのFontFamilyにRicty Diminishedを設定
  * ShowInvisiblesをチェック（半角スペース等がわかるようになる）
  * softWrapをチェック（長い行を折り返す）
  * ガイド線を消すにはInstallPackageのwrap-guideをDisableにすればよい
  * autocomplete-plusがオートコンプリート機能を提供するパッケージ

## 便利機能
  * コメントのトグル
    * Ctr + /

  * 複数選択
    * Ctr + マウスドラグ
    * Ctr + d / Ctr + k / Ctr + U / Ctr + G

  * コマンドパレット
    * Ctr Shift P

  * 検索
    * ファイル検索
      1. Ctr P
      2. ファイル名をあいまいに入力する
      3. 後ろに:10とか付加することでその行にとべる
    * 文字列検索
      * Ctr + f
      * Ctr + Shift + f プロジェクト内

  * ペイン操作
    * ペインの分割
      * Ctr + K, →
    * ペインの移動
      * Ctr + K, n
      * Ctr + K, p
    * ツリービュー操作
      * ツリービューに移動
        * Alt + \
      * ツリービューのトグル
        * Ctr + \
      * ツリービューの折り畳み、展開
        * Ctr + [
        * Ctr + ]
        * Enterで代用できた

  * ファイルを閉じる
    * Ctr + w

  * カーソルを移動
    * Ctr + G "10:8"
    * Ctr + →
    * Ctr + ←
    * Ctr + Home
    * Ctr + End
    * Ctr + M 対応するカッコ

  * 行の操作
    * 行を挿入
      * Ctr + Enter
      * Ctr + Shift+ Enter
    * 行の削除
      * Ctr + Shift + K
    * 行を複製
      * Ctr + Shift + D

### keymap.csonを変更して”Alt + ↑↓で矩形選択可能にする”
下記をkeymap.csonに追加する(http://neos21.hatenablog.com/entry/2016/01/17/035036)
~~~
# 矩形選択を Ctrl + Alt ではなく Alt だけでできるようにする : Emmet のキーバインドが重複していたので unset! で無効にする
'atom-text-editor:not([mini])':
  'alt-up': 'unset!'
  'alt-down': 'unset!'

# 矩形選択を Ctrl + Alt ではなく Alt だけでできるようにする
'body':
  'alt-up': 'editor:add-selection-above'
  'alt-down': 'editor:add-selection-below'
~~~

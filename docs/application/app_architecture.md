# アプリケーションアーキテクチャ

# 目的
+ アプリケーション設計および開発の指針を提示します。
+ アプリケーションのアーキテクチャ全体概要を理解するためのポータル的な位置づけのガイドです。
+ このガイドを起点に各々の詳細ガイドを参照してください。

# 前提
+ 対象者は、アプリ設計者・開発者です。

# 構成
+ [全体概要](#1)
+ [共通設計指針](#2)
+ [共通処理パターン指針](#3)
+ [処理パターン固有指針](#4)
+ [共通実装指針](#5)

# 詳細
## <a name="1">全体概要</a>
### 全体像
### レイヤー構造
+ モデル
+ コントローラ
+ ビュー
+ サービス

### 処理構造
+ ルーティングの基礎知識
+ モデルプレゼンター
+ フォームプレゼンター

## <a name="2">共通設計指針</a>
### 設計クラス
### データ共有方式
+ モデルオブジェクト
+ フォームオブジェクト
+ paramsオブジェクト
+ フラッシュオブジェクト
+ Errorsオブジェクト

### メッセージリソース、定数
#### デザイン
+ SCSSパーシャル
  + [色を変数で表現する](../app/assets/stylesheets/staff/_colors.css.scss)
  + [寸法を変数で表現する](../app/assets/stylesheets/staff/_dimensions.css.scss)

## <a name="3">共通処理パターン指針</a>
### データアクセス
### 例外処理
+ [クラスメソッドresucue_from](../app/controllers/application_controller.rb)
  + 500 Internal Server Error
  + 403 Forbidden
  + [404 Not Found](../app/controllers/errors_controller.rb)
  + [ActiveSupport::Concern](../app/controllers/concerns/error_handlers.rb)
+ [エラーCSS](../app/assets/stylesheets/shared/errors.css.scss)

### ログ
### セキュリティ
+ [config/secrets.ymlとシークレットキーベース](../config/secrets.yml)・・・外部APIのキーなど秘密データをここに記述する。
+ [ハッシュ関数](../app/models/concerns/password_holder.rb)
+ Strong Parameters

### 初期化
+ [シードデータの投入](../db/seeds.rb)
+ モデルオブジェクトの正規化とバリデーション

### 国際化
+ rails-i18n

### 日付処理
### 帳票出力
### 固定長データ・ファイルの扱い
### 共通機能
#### サービスオブジェクト
+ [Staff::Authenticatorクラス](../app/services/staff/authenticator.rb)

#### ヘルパークラス
+ [ヘルパーメソッドの定義](../app/helpers)

#### デザイン
+ スタイルシートの分割
  + [CSSファイル](../app/assets/stylesheets)
  + [レイアウトファイル](../app/views/layouts)
  + [アプリケーションコントローラ](../app/controllers/application_controller.rb)
+ ページネーション
+ HtmlBuilder

## <a name="4">処理パターン固有指針</a>
### Web固有
+ [リソースベースのルーティング](../config/routes.rb)

### MQ待ち受け処理固有
### バッチ処理固有
### ファイル待ち受け処理固有
## <a name="5">共通実装指針</a>

# 参照
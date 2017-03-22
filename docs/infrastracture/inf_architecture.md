# インフラストラクチャアーキテクチャ

# 目的
+ インフラストラクチャ設計および開発の指針を提示します。
+ インフラストラクチャアーキテクチャ全体概要を理解するためのポータル的な位置づけのガイドです。
+ このガイドを起点に各々の詳細ガイドを参照してください。

# 前提
+ 対象者は、インフラ設計者・開発者です。

# 構成
+ [全体概要](#1)
+ [共通設計指針](#2)
+ [実装指針](#3)
+ [実装](#4)

# 詳細
## <a name="1">全体概要</a>
### 全体像
#### 開発環境
  
  ![コンポーネント図](./development/img/components.png)

#### ステージング環境
  
  ![コンポーネント図](./staging/img/components.png)
  
  
     
## <a name="2">共通設計指針</a>
### 構築
### 開発
### 運用
## <a name="3">実装指針</a>
### 共通環境
環境ごとの環境変数の内容は以下を参照

+ [開発環境](./ops/development/config/env/system-environment-variable.sh)
+ [ステージング環境](./ops/staging/config/env/system-environment-variable.sh)
+ [プロダクション環境](./ops/production/config/env/system-environment-variable.sh)

### AWSアカウント作成
管理者権限を持つadminユーザーをマネジメントコンソールで作成して認証情報を控えておく

### 仮想マシンセットアップ
仮想マシンを最初からセットアップする場合は[開発用仮想マシン構築手順](./development/src/build/vm/README.md)を参照
仮想マシンを起動して環境構築作業用ディレクトリに移動する
```
$ git clone $DEV_APP_REPOSITORY $APPLICATION_NAME
$ cd $APPLICATION_NAME
$ cd ops
$ vagrant up
$ vagrant ssh
$ cd /vagrant/ops
```

### 環境変数をセットアップする
`.bashrc`と`.bash_profile`の最終行に以下を追記する
```
source /vagrant/ops/development/config/env/system-environment-variable.sh
source /vagrant/ops/staging/config/env/system-environment-variable.sh
source /vagrant/ops/production/config/env/system-environment-variable.sh
```
設定が終わったら一度仮想マシンからログアウトして最後ログイン後に環境変数変数が反映されているか確認する  
```
$ exit
$ vagrant ssh
$ env
```

## <a name="4">実装</a>
### [開発環境](./development/README.md)
### [ステージング環境](./staging/README.md)
### [プロダクション環境](./production/README.md)

# 参照
+ [PlantUML](http://www.plantuml.com)
+ [PlantUML online demo server](http://www.plantuml.com/plantuml/uml/SyfFKj2rKt3CoKnELR1Io4ZDoSa70000)

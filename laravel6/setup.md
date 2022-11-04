# Laravel6 環境構築(セットアップからブラウザでの動作確認まで)

Laravel6系を使用する。
PHPのバージョンは7.2 ~ 8.0系である必要がある。
構築が完了すると
usersテーブルの作成がされた状態になる。

セットアップ済みの内容は以下。READMEを参考にしてすぐに構築できる。
[toshi-ue/laravel-6-template](https://github.com/toshi-ue/laravel-6-template)

## 動作環境

Column | Column B |
---------|----------|
macOS | BigSur |
PHP |8.0.23|
Laravel|6.20.26|
MySQL|5.7系|

## 手順

### composerのインストール

TODO: composerのインストール手順を追加

### PHPのインストール

TODO: PHPのインストール手順を追加

### Sqliteのインストール

TODO: Sqliteのインストール手順を追加

### MySQLのインストール

TODO: MySQLのインストール手順を追加
> [MySQLデータベースを使ってLaravel構築 in Mac | アールエフェクト](https://reffect.co.jp/laravel/mysql-laravel-in-mac)

### プロジェクトの作成

```bash
mkdir sampleapp && cd $_;
composer create-project --prefer-dist laravel/laravel . "6.*";
```

### データベースの作成

データベースをGUIもしくはCUIで作成する。
作成しないとユーザーテーブルの作成ができない。
データベースを作成し、`.env`ファイルの`DB_DATABASE`を作成したデータベース名と同じに変更する。

> [【Laravel】MySQLの接続方法を徹底解説【コピペでOK】](https://yaba-blog.com/laravel-db/)
> [MySQLデータベースを使ってLaravel構築 in Mac | アールエフェクト](https://reffect.co.jp/laravel/mysql-laravel-in-mac)

### ユーザーテーブルの作成

プロジェクト作成後に以下コマンドを実行することによって自動的にusersテーブルが作成される（ファイルはプロジェクト作成時にすでに作成されている）。

```bash
php artisan migrate;
```

### ビルトインサーバの起動ブラウザで動作確認

terminalで以下のコマンドを実行してビルトインサーバを起動し、ブラウザのurl欄に`localhost:8000`または`http://127.0.0.1:8000`を入力してアクセスする。ブラウザでLaravelと表示されればok

```bash
php artisan serve;
```

### Laravel/uiをインストール（ユーザー認証機能を追加）

Auth（ユーザーログイン）機能は`Laravel/ui`パッケージに同梱されている。
以下のコマンドでインストールする（Laravel6はバージョン指定が必要）。

```bash
composer require laravel/ui 1.*
```

### Auth関連ファイルを作成、インストールする

以下のコマンドで関連ファイルが作成される

```bash
# 以下の3つのどれかからコマンドを選ぶ(BootStrap4のみ or Vue .js(2)+BootStrap4 or React.js+BootStrap4)
php artisan ui bootstrap --auth;
php artisan ui vue --auth;
php artisan ui react --auth;
npm install --legacy-peer-deps;
```

> [Laravel 6系でmake:authを使う方法 - Qiita](https://qiita.com/rei67/items/d6d0f5f6e58edbb17c09)

## 参考

- [Laravelのログイン認証の基本(Authentication)を完全理解する | アールエフェクト](https://reffect.co.jp/laravel/laravel-authentication-understand)
- [Laravel6.x以降でログイン機能をインストールする方法 – console dot log](https://blog.capilano-fw.com/?p=4576)
- [[Laravel]6.x系で認証機能をサクッと動かす | コードライク](https://codelikes.com/laravel-use-auth/)
- [Laravel6 ログイン機能を実装する - Qiita](https://qiita.com/ucan-lab/items/bd0d6f6449602072cb87)
- > [Laravel+PostgreSQL+Vue.jsでSPA開発【チュートリアル】 - OPTiM TECH BLOG](https://tech-blog.optim.co.jp/entry/2019/08/13/173000)

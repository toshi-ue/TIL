# vue-routerの追加

Laravel6 x Vue2へvue-routerを追加する。<br>
以下を参考にすればできる。これが一番よさそう。<br>
> [Laravel6.xとvue.jsのVue RouterでSPA構築 | アールエフェクト](https://reffect.co.jp/laravel/laravel-vue-router-single-page-application)

下記リンクは`vue2` + `vue-router@3`をインストールしたリポジトリ。
テンプレートを使用してプロジェクトを新規作成、以下の手順を踏めばすぐにプロジェクトを開始、動作確認できる。

[toshi-ue/laravel6-vue-boilerplate](https://github.com/toshi-ue/laravel6-vue-boilerplate)

1. プロジェクトを作成（テンプレートを使用して、新しいプロジェクトを作成）
2. git cloneを行う
3. 以下のコマンドを実行

```bash
git fetch --depth 1 origin 3f1a1a3a75062227cbac3941d07278ba6a9a355b;
git reset --hard FETCH_HEAD;
composer update;
composer install;
cp .env.example .env;
php artisan key:generate;
npm install --legacy-peer-deps;
```

## 注意点、変更点

### Laravelのインストール

Laravel6の場合は以下のようにバージョン指定が必要（要確認）。

```bash
composer create-project --prefer-dist laravel/laravel <プロジェクト名> "6.*"
```

### Vueのインストール

Laravel6の場合は以下のようにバージョン指定が必要（要確認）。

```bash
composer require laravel/ui:1.*
```

### Vue Routerのインストール

Vue2の場合はバージョン指定が必要。

```bash
npm install vue-router@3 --legacy-peer-deps
```

# vue-i18n

Vue.jsの多言語化のためのライブラリ。
> [kazupon/vue-i18n: Internationalization plugin for Vue.js](https://github.com/kazupon/vue-i18n)

## 問題点

VeeValidateの多言語化ができていない

## 動作環境

22/10/15
Column A | Column B |
---------|----------|
 macOS | BigSur |
 Vue | 2.5.17 |
 vue-i18n| 8.27.2|
 PHP |8.0.23|
 Laravel|6.20.26|

## vue-i18nをインストール

vue-i18nをインストール。`--legacy-peer-deps`が必要になる場合がある。

```bash:terminal
npm install vue-i18n@8 --legacy-peer-deps
```

### 設定

以下を`resources/js/app.js`に追記する

```javascript
// import Vue from 'vue'; 以降に記述
import VueI18n from "vue-i18n";

// FIXME: VueI18nを追加するとエラーが発生する、いろんな箇所に影響が出るため現在はコメントアウト。developmentでは動作してくれている
//      ↓↓追加
// Vue.use(VueI18n, VueRouter);
Vue.use(VueRouter);

// 追記
const i18n = new VueI18n({
    // デフォルト言語(どちらかを選択)
    //  [【Vue.js】vue-i18n を使用した国際化（多言語）対応 - 山崎屋の技術メモ](https://www.shookuro.com/entry/2019/08/30/181143#:~:text=%E3%82%A4%E3%83%B3%E3%83%9D%E3%83%BC%E3%83%88%E3%81%99%E3%82%8B%E3%80%82-,new,-Vue%20%E3%81%97%E3%81%A6)
    locale: "ja",
    // locale: navigator.language.split('-')[0], // 追加
    // ブラウザの言語設定がいずれにも一致しなければfallbackLocaleに設定された言語が表示される。
    //  [nuxt-i18nで日本語と英語に対応する | nansystem](https://nansystem.com/nuxti18n/#defaultlocale%E3%82%AA%E3%83%95%E3%82%9A%E3%82%B7%E3%83%A7%E3%83%B3)
    fallbackLocale: "en",
    messages: {
        // [【Vue.js】vue-i18nを使って多言語化 - Qiita](https://qiita.com/shin_moto/items/505ae84e9a37601e05ee#:~:text=%E3%81%BE%E3%81%9A%E3%81%AF%E3%83%A9%E3%82%A4%E3%83%96%E3%83%A9%E3%83%AA%E3%82%92-,%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB,-npm%20install%20vue)
        en: require("../lang/en.json"),
        ja: require("../lang/ja.json"),
    },
});
```

### 言語ファイルの追加

`resources/lang/en.json`、`resources/lang/ja.json`を追加する。
`resources/lang/en.json`

```json
{
    "task": {
        "description": "Description",
        "done": "Done",
        "status": {
            "undone": "undone",
            "completed": "completed"
        },
    }
}
```

`resources/lang/ja.json`

```json
{
    "task": {
        "description": "詳細",
        "done": "進捗",
        "status": {
            "undone": "未完了",
            "completed": "完了"
        },
    }
}
```

### テンプレートファイルでの書き方

sample.vue

```javascript
<template>
<label for="description">{{ $t("task.description" )}}</label>
// [Vue.js: Vue I18nの公式ドキュメントに見当たらず悩んだふたつのこと - Qiita](https://qiita.com/FumioNonaka/items/138a60f4472ece69c192)
<input type="text"
  v-model="task.description"
  :placeholder="$t('task.description')"
/>

// selectbox
<select
  name="done"
  id="done"
  class="col-sm-9 form-control"
  v-model="task.done"
>
  <option value="0" v-bind:selected="task.done">
    {{ $t("task.status.undone") }}
  </option>
  <option value="1" v-bind:selected="task.done">
    {{ $t("task.status.completed") }}
  </option>
</select>
</template>
```

### 以上

終了。

### 参考

公式。Vue.js2.x用のためのライブラリ。3系はver9
> [Introduction | Vue I18n](https://kazupon.github.io/vue-i18n/introduction.html#sponsors)
>
簡潔でわかりやすい
> [【Vue.js】vue-i18n を使用した国際化（多言語）対応 - 山崎屋の技術メモ](https://www.shookuro.com/entry/2019/08/30/181143)
> [Laravel で Vue を利用する際の Tips/メモ - to-me-mo-rrow - 未来の自分に残すメモ -](https://r17n.page/2020/08/29/php-laravel-with-vue/)

言語ファイルは以下を参考にして作成
> [【Vue.js】vue-i18nを使って多言語化 - Qiita](https://qiita.com/shin_moto/items/505ae84e9a37601e05ee)

nuxtだが設定は参考にできそう
> [nuxt-i18nで日本語と英語に対応する | nansystem](https://nansystem.com/nuxti18n/)

ページのタイトルの多言語化は以下を参考にすると良いかもしれない
> [vue-i18n の簡易入力補完を実装してみた雑感 | For X Developers](https://blog.tanaka.world/vue-i18n-autocompletion/)

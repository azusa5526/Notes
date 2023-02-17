# Vue 3 專案目錄結構

記錄專案目錄結構規則

&emsp;

# ASCII Tree
```
src
├── api
│   ├── request.ts
│   └── user.ts
├── assets
│   ├── img
│   └── svg
├── components
│   └── SvgIcon.vue
├── layouts
│   ├── components
│   │   ├── LayoutAppBar.vue
│   │   ├── LayoutContent.vue
│   │   ├── LayoutFooter.vue
│   │   └── LayoutNavDrawer.vue
│   ├── LayoutBlank.vue
│   └── LayoutPrimary.vue
├── plugins
│   ├── index.ts
│   ├── vite-plugin-svg-sprite.js
│   ├── vuetify.ts
│   └── webfontloader.ts
├── router
│   └── index.ts
├── store
│   ├── app.ts
│   └── index.ts
├── styles
│   ├── global.scss
│   ├── settings.scss
│   └── style.css
├── utils
│   └── index.ts
├── views
│   └── home
│       ├── HelloWorld.vue
│       └── Home.vue
├── App.vue
├── main.ts
└── vite-env.d.ts
```

<details>
<summary>api - 依據功能分割的 api 請求方法，以及放置攔截器</summary>
<br>

request.ts - axios 攔截器

user.ts - 範例 api 請求方法
</details>

<details>
<summary>assets - 靜態資源 </summary>
<br>

img - 需被編譯，但不需經過 svg-sprite plugin 處理的影像檔案

svg - 需被編譯，且需經過 svg-sprite plugin 處理的 svg 檔案
</details>

<details>
<summary>components - 共用組件 </summary>
<br>

SvgIcon.vue - svg-sprite 實現組件
</details>

<details>
<summary>layouts - 預製布局</summary>
<br>

components - 放置用來組合預製布局的小元件

LayoutPrimary.vue - 預設提供的基本布局

LayoutBlank.vue - 預設提供的空白布局
</details>

<details>
<summary>plugins - vue / vite 插件</summary>
<br>

index.ts - 插件統一插入點

vuetify.ts - vuetify 插件配置點

webfontloader.ts - 網路字形插件配置點

vite-plugin-svg-sprite - vite svg-sprite 插件本體
</details>

<details>
<summary>router - 前端路由</summary>
<br>

index.ts - 路由進入點

nav-guard.ts - 全域導航守衛
</details>

<details>
<summary>store - pinia 狀態管理</summary>
<br>

index.ts - pinia 進入點

app.ts - 預設 pinia module
</details>

<details>
<summary>styles - css / scss</summary>
<br>

settings.scss - vuetify scss variable 覆蓋點

global.scss - 自定義全域的 scss 樣式

style.css - tailwind css 引入設置
</details>

<details>
<summary>utils - js / ts 工具庫</summary>
<br>

index.ts - 範例檔案
</details>

<details>
<summary>views - 路由使用或獨立頁面的元件，使用資料夾區分，進入點與資料夾同名，並使用大駝峰命名，同層放置會使用到的周邊元件</summary>
<br>

<details>
<summary>home - 範例資料夾</summary>
<br>

Home.vue - 範例進入點

HelloWorld.vue - 範例周邊元件
</details>

</details>
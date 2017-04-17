# vue-boilerplate

> vue-boilerplate

## 开发、测试、打包命令

``` bash
# install dependencies
yarn install

# serve with hot reload at localhost:8080
yarn run dev

# build for production with minification
yarn run dist

# run unit tests
yarn run unit

# run all tests
yarn test
```

## 工作流

### 技术栈：

+ Vue 2 （https://cn.vuejs.org/）
+ vue-router (搭配 Vue 的路由库)
+ less (CSS 编写方案）
+ Vue scoped style （CSS 模块化方案）
+ isomorphic-fetch （fetch polyfill）
+ ...

### 开发工具：

+ yarn
+ babel
+ webpack
+ eslint (airbnb-base)
+ karma + mocha + phantomjs
+ ...

### 推荐的编辑器：

VSCode

### 推荐的插件：

+ Add New Line to Files

+ Auto Rename Tag

+ HTML CSS Support

+ HTML Snippets

+ Path Intellisense

+ ...

### 源码目录 /src ：

```
/assets       其他静态资源
/components   少量的公共组件
/styles       少量的全局样式和公共样式
/views        主要的视图页面
App.vue       整个应用的容器
main.js       入口文件
routes.js     路由表
```

整个应用分为 `左侧导航栏` 与 `右侧主视图`，主要开发任务集中在 主视图（/views） 上；

容器 = 导航栏 + 主视图；

主视图 的变换由 `路由表` 控制，不同路由展示不同视图；

/views 目录下，每个 .vue 文件对应一个视图页面；

每个视图页面中有 `模板、脚本、样式` 三部分。

### 协作要求：

为方便协作开发，预先约定如下：

+ 样式编写使用 less
+ 局部样式：每个 视图/组件 的样式写在各自文件的 `<style lang="less" scoped></style>` 标签中，其为局部作用域，仅对当前文件有效；所以 className/tagName 随意命名，不用担心与其他样式冲突
+ 公共样式：可在 /styles 下增加公共的 .less 文件，然后在 .vue 视图文件的样式标签中手动 `@import` 加载
+ 全局样式：已全局加载，必须写在 /styles/global/ 下，并且 className 必须有 `global--` 前缀。其 className 可在任何模板中使用
+ 第三方全局样式：可能会引入一些第三方 .css 文件，在 /main.js 入口文件中使用 `require('xxxx)` 全局加载
+ 其他资源：.less/.js/.vue 以外的资源放在 /assets 下的分类目录中，如图片放在 /assets/images

### 文件的引入方式：

`src` 已添加到 webpack 别名，别名为 `@`，可以这样使用：

.js : `import xxx from '@/utils/xxx'`

.vue : `import xxxx from '@/components/xxxx'`

.css :（来自于 node_modules 的外部文件）

        在 /main.js 入口文件中使用 `require('xxxxx.css')` 全局引入

.less :

        全局引入：在 /main.js 入口文件中使用 `require('xxxx.less)`

        局部引入：在 .vue 文件的 <style> 标签中，或 .less 文件中：使用 `@import "~@/styles/xxx.less";`

svg/png/eot/json/other :

        在 .vue 文件的 <style> 标签中，或 .less 文件中：使用 `background: url(~@/assets/images/xxx.png);`
        
        在 js 代码中推荐使用 `const xxx = require('@/assets/images/xxx.png')` [ * 当然你要是想用 import xxx from '@/assets/images/xxx.png' 也可以，但 require 更加清楚地表明了这是 webpack 的能力，所以更推荐前者 ]

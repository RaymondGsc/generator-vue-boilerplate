# vue-boilerplate

>  基于Vue2.0的前端脚手架

## 开发、测试、打包命令

``` bash
# install dependencies
yarn install

# serve with hot reload at localhost:8080
yarn start

# build for production with minification
yarn run dist

# run unit tests
yarn run unit

# run all tests
yarn test
```

## 工作流

### 技术栈：

+ Vue 2 （http://cn.vuejs.org/）
+ vue-router
+ less
+ Vue scoped style
+ isomorphic-fetch
+ ...

### 开发工具：

+ yarn
+ babel
+ eslint(airbnb-base)
+ karma + mocha + phantomjs
+ ...

### 推荐的编辑器：

VSCode 1.8.1+

### 推荐的插件：

+ Vetur

+ Vue Components

+ Add New Line to Files

+ Auto Rename Tag

+ HTML CSS Support

+ HTML Snippets

+ Path Intellisense

+ ...

### 源码目录 /src ：

```
/assets       其他资源
/components   少量的公共组件
/styles       少量的公共样式或变量
/views        主要的视图页面
/utils        应用函数的打包
App.vue       整个应用的容器
index.html    渲染平台
main.js       入口文件
routes.js     路由表
```

### 协作要求：

为方便协作开发，预先约定如下：

+ 样式编写使用 less
+ 局部样式：每个 视图/组件 的样式写在各自文件的 `<style lang="less" scoped></style>` 标签中，其为局部作用域，仅对当前文件有效；所以 className/tagName 随意命名，不用担心与其他样式冲突
+ 公共样式：可在 /styles 下增加公共的 .less 文件，然后在 .vue 视图文件的样式标签中手动加载
+ 全局样式：已全局加载，必须写在 /styles/global 文件夹中，并且 className 必须有 `global--` 前缀。其 className 可在任何模板中使用
+ 第三方全局样式：可能会引入一些第三方 .css 文件，在 /main.js 入口文件中使用 `require('xxxx)` 全局加载
+ 其他资源：.less/.js/.vue 以外的资源放在 /assets 下的分类目录中，如图片放在 /assets/images

### 文件的引入方式：

assets,components,styles,views 已添加到 webpack 别名，除了 less import 以外均可使用别名路径

.js : `import xxx from 'xxx/xxx'`

.vue : `import xxxx from 'xxx/xxx.vue'`

.less : `@import "../styles/xxx";`

.css :  `require('xxxx)` 在 /main.js全局加载（来自于 node_modules 的外部文件）

其他资源 :
        
        在 .vue 文件的样式标签中使用类似 `background: url(~assets/images/xxx.png);`
        在 js 代码中推荐使用 `const xxx = require('assets/images/xxx.png')`

Vue2.0 搭建脚手架 

**概念**

  Vue-cli 是 Vue 官方提供的用于初始化 Vue 项目的脚手架工具。使用 Vue-cli 有以下几大优势

  1、Vue-cli 是一套成熟的 vue 项目架构设计，会跟着 Vue 版本的更迭而更新

  2、Vue-cli 提供了一套本地的热加载的测试服务器

  3、Vue-cli 集成了一套打包上线的方案，可使用 webpack 或 Browserify 等构建工具

```shell
# 查看node版本
node -v
# 查看npm 版本
npm -v
# 更新node.js版本
#1.清除npm缓存
npm cache clean -f 
#2.安装n模块，n模块是专门用来管理nodejs版本 --force或-f:强制重新安装
npm install -g n -f
#3.升级node.js到最新稳定版
n stable 
#查看node安装路径
which node
#直接升级最新版本
npm install npm @latest -g
# windows 版本直接重装吧！

#安装cnpm 使用国内淘宝源
npm install -g cnpm --registry=https://registry.npm.taobao.org
# nvm 管理包版本
#全局安装 webpack 
npm install webpack -g
# 安装完成后输入 webpack -v，出现对应版本号则安装成功。
npm install webpack-cli -g
# Vue 安装
# 最新稳定版
$ npm install vue
#安装vue-cli脚手架构建工具 2.9.6
cnpm install --global vue-cli
# 查看版本
vue -V
# 创建一个基于 webpack 模板的新项目 taopiaopiao
vue init webpack  taopiaopiao
Project name (taopiaopiao) # 项目名称（我的项目）
Project description (A Vue.js project) # 项目描述一个Vue.js 项目
Author 作者（你的名字）
Install vue-router? (Y/n) # 是否安装Vue路由，也就是以后是spa（但页面应用需要的模块）
Use ESLint to lint your code? (Y/n) # 使用 ESLint 到你的代码？ （Y [ yes ] / N [ no ]）
Pick an ESLint preset (Use arrow keys) # 选择一个预置ESLint（使用箭头键）
Setup unit tests with Karma + Mocha? (Y/n) # 设置单元测Karma + Mocha？ （Y/ N）
Setup e2e tests with Nightwatch? (Y/n) # 设置端到端测试，Nightwatch？ （Y/ N）
#安装项目所需要的依赖
cnpm i
#运行项目
cd tiaopiaopiao
npm run dev
# Vue CLI 3.0 搭建
# 1.如果你Vue2.9.6未安装跳过此步骤，已经安装了vue 2.9.6 的话，则需要先将其删除：指令为：
npm uninstall -g vue-cli 
# 提示：Vue CLI要求Node.js版本8或者更高（8.10.0+ 推荐）。
# 更新Vue-cli 指令：(` cnpm install -g @vue/cli ` 使用国内的淘宝镜像cnpm 安装速度快)
npm install -g @vue/cli 或 cnpm install -g @vue/cli 或 yarn global add @vue/cli 
# 构建项目 3.0 预设 presets  2.0 是要选择模板；指令：
vue create maoyan
# 默认配置
#	选择 [默认] 将直接开始安装 
# 自定义配置
#    选择 [自定义] 
#    方向键上下移动，空格选中，Enter确定，自定义配置中，您将会看到这些配置项
# 自定义细节配置
# 1.是否使用class风格的组件语法 
# 2.是否使用babel做转义
# 3.选择CSS预处理类型 
# 4.选择语法检测规范
# 5.选择 保存时检查 / 提交时检查 
# 6.选择配置信息存放位置，单独存放或者并入package.json 
# 7.是否保存当前预设，下次构建无需再次配置 

```

#### 两个版本的差异

- public相当于原来的static，里面的index.html是项目的入口 
- src同以前一样
- Vue-Cli3.0没有build和config了， 想要配置的话，需要在项目根目录下创建vue.config.js文件 

使用 vue.config.js 文件（位置是项目的根目录，不是src目录）

```js
module.exports = {
 // 基本路径
 baseUrl: '/',
 // 输出文件目录
 outputDir: 'dist',
 // eslint-loader 是否在保存的时候检查
 lintOnSave: true,
 // use the full build with in-browser compiler?
 // https://vuejs.org/v2/guide/installation.html#Runtime-Compiler-vs-Runtime-only
 compiler: false,
 // webpack配置
 // see https://github.com/vuejs/vue-cli/blob/dev/docs/webpack.md
 chainWebpack: () => {},
 configureWebpack: () => {},
 // vue-loader 配置项
 // https://vue-loader.vuejs.org/en/options.html
 vueLoader: {},
 // 生产环境是否生成 sourceMap 文件
 productionSourceMap: true,
 // css相关配置
 css: {
  // 是否使用css分离插件 ExtractTextPlugin
  extract: true,
  // 开启 CSS source maps?
  sourceMap: false,
  // css预设器配置项
  loaderOptions: {},
  // 启用 CSS modules for all css / pre-processor files.
  modules: false
 },
 // use thread-loader for babel & TS in production build
 // enabled by default if the machine has more than 1 cores
 parallel: require('os').cpus().length > 1,
 // 是否启用dll
 // See https://github.com/vuejs/vue-cli/blob/dev/docs/cli-service.md#dll-mode
 dll: false,
 // PWA 插件相关配置
 // see https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-pwa
 pwa: {},
 // webpack-dev-server 相关配置
 devServer: {
  open: process.platform === 'darwin',
  host: '0.0.0.0',
  port: 8080,
  https: false,
  hotOnly: false,
  proxy: null, // 设置代理
  before: app => {}
 },
 // 第三方插件配置
 pluginOptions: {
  // ...
 }
}
```

`npm run serve`   ——运行指令 
`npm run lint` ——语法检测&自行修复
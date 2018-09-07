# Webpack学习笔记
项目初始化
> npm i

创建项目基础文件夹和文件

```
|--config
|----webpack.base.config.js
|----webpack.dev.config.js
|--index.js
|--index.html
...
```
安装依赖包
> npm install `html-webpack-plugin webpack webpack-cli webpack-dev-server` --save-dev

> npm install `css-loader style-loader vue vue-loader` --save

或者通过yarn安装依赖
> yarn add `html-webpack-plugin webpack webpack-cli webpack-dev-server` --dev

> yarn add `css-loader style-loader vue vue-loader`

配置webpack.base.config.js
```
const path = require('path');

module.exports = {
  mode: 'development',
  entry: {
    app: './index.js' // 入口js
  },
  output: {
    path: path.join(__dirname, '../dist'), // 打包输出路径
    filename: '[name].js' // 打包输出文件名字 name 对应的是 entry 里面的 app
  }
}
```
配置package.json打包命令
```
"scripts": {
    "build": "webpack--config./config/webpack.base.config.js"
}
```
运行`npm run build`，会自动生成dist文件夹并生成js文件

添加html-webpack-plugin到配置文件
<pre><code>
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin')

module.exports = {
  mode: 'development',
  ...
  plugins: {
    new HtmlWebpackPlugin({
      filename: 'index.html', // html文件名
      template: 'index.html', // 指定文件模板
      inject: true // 是否引用打包好的js
    })
  }
}
</code></pre>

安装 webpack
npm install webpack -g

webpack 也有一个 web 服务器 webpack-dev-server, 我们也安装上
npm install webpack-dev-server -g

运行 webpack 打包, 运行 webpack-dev-server 启动服务器.

配置 package.json
在项目根目录下运行 npm init -y 会按照默认设置生成 package.json, 修改 scripts 的键值如下:
"scripts": {
  "start": "webpack-dev-server",
  "build": "webpack"
}
现在执行 npm run build 相当于 webpack, npm run start 相当于 webpack-dev-server.

安装 React
npm install react react-dom --save

为了简化 AJAX 请求代码, 这里引入 jQuery
npm install jquery --save

安装 Babel 的 loader 以支持 ES6 语法
npm install babel-core babel-loader babel-preset-es2015 babel-preset-react --save-dev
配置 webpack.config.js 来使用安装的 loader
<!--
  var path = require('path');
  module.exports = {
    entry: path.resolve(__dirname, './app/app.js'),
    output: {
      path: path.resolve(__dirname, './build'),
      filename: 'bundle.js'
    },
    module: {
      loaders: [
      {
        test: /\.jsx?$/,
        exclude: /node_modules/,
        loader: 'babel',
        query: {
          presets: ['es2015','react']
        }
      },
      ]
    }
  };
-->
在开发时我们还会涉及其他的资源文件, 如图像, 字体, 样式等, 它们也需要被模块化,因此要安装对应的 loader
npm install url-loader file-loader --save-dev
配置 webpack.config.js
//...
 loaders: [
 //..
 {
   test: /\.(png|jpg|gif)$/,
   loader: 'url-loader?limit=8192'// 这里的 limit=8192 表示用 base64 编码 <= ８K 的图像
 }]
//...

我们也需要将样式模块化,安装相应的 loader
npm install css-loader style-loader --save-dev
css-loader 处理 css 文件中的 url() 表达式,style-loader 将 css 代码插入页面中的 style 标签中
在 webpack.config.js 中配置新的 loader.
{
 test: /\.css$/,
 loader: 'style!css'
}

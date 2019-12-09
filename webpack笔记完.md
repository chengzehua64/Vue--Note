## 一、webpack是什么:

```
  webpack是一款静态资源打包构建工具

   常用构建工具：grunt,gulp,webpack...

```

## 二、webpack在前端中的作用:

   webpack主要用于前端环境搭建(基于nodejs)，模块化开发等

## 三、webpack如何使用

   第一步：创建package.json文件

      npm init -y
   第二步：初次用webpack玩一把构建

    首先安装webpack相关包：

    npm i webpack webpack-cli -D

    安装好后，在package.json中文件如下：

    {
      ...
      "devDependencies": {
         "webpack": "^4.41.2",
         "webpack-cli": "^3.3.10"
      }
      }

   可以通过直接在命令行方式下直接执行：webpack回车即可构建

   入口文件：自动去找src/index.js
   构建后的目录：dist,生成的文件名main.js

   可以通过配置文件来构建打包：webpack.config.js (项目根目录下)

   当然配置文件名可以单独指定其他文件名，执行时，通过：

   webpack --config 要执行的配置文件名

   例如：webpack --config webpack.prod.config.js

   删除打包后无用的文件：

     npm install clean-webpack-plugin;

   在webpack.config.js引入并导入到plugin中，例如：

const { CleanWebpackPlugin }=require('clean-webpack-plugin')

//webpack配置项
const config = {
    ....
    plugins: [
       ,
        new CleanWebpackPlugin(),
    ]

}

   Loader:本质上就是将webpack不能识别的文件类型转换成为可以被识别的文件类型

    css的loader:style-loader,css-loader,
    sass的loader:sass-loader,node-sass
    svg,eot,ttf:file-loader,url-loader
    less的loader:less-loader,less
    ........

    那如何配置loader???   在webpack.config.js文件中添加

    ....
    module: {
        rules: [
            { test: /\.css$/, use: ['style-loader', 'css-loader'] },
            { test: /\.s[ac]ss$/, use: ['style-loader', 'css-loader', 'sass-loader'] },
            { test: /\.vue$/, use: ['vue-loader'] },
            {
              test: /\.css$/,
              use: [
                'vue-style-loader',
                'css-loader'
              ]
            },
            
            {
                test: /\.js$/,
                use: 'babel-loader',
                exclude: /node_modules/
            }

       ]
    }

    ...

    如何配置默认省略的文件类型：在webpack.config.js文件中添加

 ```
    resolve: {
        extensions:['.js','.vue']
    }
    
```


   



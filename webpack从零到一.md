```
npm init
```

初始化webpack文件，按照提示一路回车下来，得到这样一个package.json文件

```
{
  "name": "webpack-study",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}

```

```
cnpm install webpack webpack-cli -g
```

不推荐全局安装webpack及其脚手架

项目内安装

```
cnpm install webpack webpack-cli -D
```

指定版本安装

```
cnpm install webpack@4.34.0 webpack-cli -D
```

新建webpack.config.js,整个项目文件夹下

![1560694020159](C:\Users\Arslan\AppData\Roaming\Typora\typora-user-images\1560694020159.png)

```
const path = require('path');
module.exports={
    //区分生产环境还是线上环境
    mode:'production',
    //打包入口
    entry:'./src/index.js',
    //打包输出文件
    output:{
        //输出文件名
        filename:'dist.js',
        //输出文件路径,根目录下dist文件夹下
        path: path.resolve(__dirname, './dist')
    }
}
```

这时候我们在package.json文件夹下添加一句命令

![1560694098490](C:\Users\Arslan\AppData\Roaming\Typora\typora-user-images\1560694098490.png)

然后我们就可以在命令行输入npm  run build 执行打包了。

![1560694374466](C:\Users\Arslan\AppData\Roaming\Typora\typora-user-images\1560694374466.png)

跟我们在使用vue和react脚手架内置的命令打包时很像，但是少了个index.html文件无法运行打包出来的js文件，这时候我们需要一个插件

```
HtmlWebpackPlugin
```

```
cnpm install --save-dev html-webpack-plugin
```

```
const HtmlWebpackPlugin = require('html-webpack-plugin');
const path = require('path');
module.exports = {
    //区分生产环境还是线上环境
    mode: 'production',
    //打包入口
    entry: './src/index.js',
    //打包输出文件
    output: {
        //输出文件名
        filename: 'dist.js',
        //输出文件路径,根目录下dist文件夹下
        path: path.resolve(__dirname, './dist')
    },
    //新增的插件
    plugins: [new HtmlWebpackPlugin(
        {
            template: './src/index.html'
        }
    )]
}
```

这时我们src文件夹新建一个index.html文件引入index.js

这时候我们再执行打包命令就会看dist文件夹自动生成了一个index.html。用浏览器打开文件发现，js语句正常运行。


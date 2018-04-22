## 零配置快速构建

> 创建文件夹

    `mkdir webpack-4-quickstart && cd $_`

>  初始化

`npm init -y`

> 安装依赖

`npm i webpack-cli --save-dev`
`npm i webpack --save-dev`

> 增加快速构建

在package.json中添加build命令
`"scripts": {
  "build": "webpack"
}`

> 注意

webpack4.0后默认必须
在根目录新建./src/index.js为默认，否则无法build

> 实例

1. 新建./src/index.js，内容为console.log('test build');
2. `npm run build`后将在根目录生成dist/main.js

## 生产环境和开发环境的mode

> 风格

webpack4.0有两种项目风格
1.a configuration file for development
2.a configuration file for production

> 设置项目打包环境

在package.json中添加命令，区分dev，和product
`"scripts": {
  "dev": "webpack --mode development",
  "build": "webpack --mode production"
}`

> 特点

`npm run dev`得到的模块是未压缩的
`npm run build`得到的模块是压缩后的

## 修改默认输入输出文件

> 特点

webpack的零配置优点显著，但如何自定义导入导出文件目录

> 自定义导入导出

配置package.json

```
"scripts": {
    "dev": "webpack --mode development ./test/from/js/index.js --output ./test/to/main.js",
    "build": "webpack --mode production ./test/from/js/index.js --output ./test/to/main.js"
}
```

## 添加babel

> 引言

并不是所有浏览器都能能好支持es6特性，webpack自身不具备将es6或者更高ECMAscript转换成es5，但webpack提供loader可以将其转换成es5特性。尽管webpack零配置的特性，但是对于loader的使用任然需要通过配置来发挥其特效

> 安装依赖

* babel-core
* babel-loader
* babel-preset-env for compiling Javascript ES6 code down to ES5

`npm i babel-core babel-loader babel-preset-env --save-dev`

> 配置

新建 .babelrc文件名，并且在文件中添加

```
{
    "presets": [
        "env"
    ]
}
```

webpack提供两种配置babel的方式:
1. 使用配置文件
2. 使用--module-bind在npm脚本中



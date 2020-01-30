webpack
=======
一、什么是webpack
------

>>WebPack可以看做是模块打包机：它做的事情是，分析你的项目结构，找到JavaScript模块以及其它的一些浏览器不能直接运行的拓展语言（Scss，TypeScript等），并将其转换和打包为合适的格式供浏览器使用。

二、webpack和Gulp/Grunt的区别
-----

>>Webpack和另外两个并没有太多的可比性，Gulp/Grunt是一种能够优化前端的开发流程的工具，而WebPack是一种模块化的解决方案，不过Webpack的优点使得Webpack在很多场景下可以替代Gulp/Grunt类的工具。

三、功能
-----
>>Webpack的工作方式是：把你的项目当做一个整体，通过一个给定的主文件（如：index.js），Webpack将从这个文件开始找到你的项目的所有依赖文件，使用loaders处理它们，最后打包为一个（或多个）浏览器可识别的JavaScript文件	

四、安装
--------

### 全局安装
>> npm install -g webpack

### 安装到你的项目目录
>>npm install --save-dev webpack

>npm运行webpack可能会提示需要安装webpack-cli，npm还懂事的询问用户是否自动安装，，，确认yes npm安装，结果一直提升需要安装webpack-cli，然后请教了度娘，webpack版本问题：“在webpack 3中，webpack本身和它的CLI以前都是在同一个包中，但在第4版中，他们已经将两者分开来更好地管理它们。

https://www.jianshu.com/p/826e9c9b9557”

>cnpm全局安装webpack-cli，再-v，如果不行再全局安装下webpack，就ok了

#### 再加一句：

>之后再cmd运行webpack -v/-h的时候会报错Error: Cannot find module 'locate-path'，一边找方法，一边瞎鼓捣，发现在c:\Users\你的计算机名称（这个就是ctrl+r后打开cmd时候的路径）里面会报这个错，而在D:E:盘里会正常显示版本号，，，反正也不在c盘放工作项目，这个问题就先放着了，以后知道问题解决方法后会来补充

五、运行
-----
 >>* ①、在需要的文件夹中创建一个package.json文件，这是一个标准的npm说明文件，里面蕴含了丰富的信息，包括当前项目的依赖模块，自定义的脚本任务等等。在终端中使用npm init命令可以自动创建这个package.json文件
npm init
输入后会问一些项目详细信息，不准备在npm发布，就一直回车就行
 >>* ②、webpack {entry file} {destination for bundled file}
`# {extry file}`处填写入口文件的路径，本文中就是上述main.js的路径，
`# {destination for bundled file}`处填写打包文件的存放路径
`#` 填写路径的时候不用添加{}

>>eg：webpack app/main.js public/bundle.js

>>非全局安装：node_modules/.bin/webpack app/main.js public/bundle.js

参考文章：https://segmentfault.com/a/1190000006178770

一、思否		路径：https://segmentfault.com/a/1190000006178770#articleHeader2
-----------

>1、npm init创建package.json配置文件

>2、npm 安装webpack，具体方法或者坑可以查看之前的写webpack

>3、搭建文件
>>main为入口文件，用require来接收/导入文件
>>greeter里面来搞事情，用express暴露出去
>>public为项目的文件，完了把项目打包后的js导入里面





>4、

>>1）html无所谓写什么

>>2）main：

```javascript
const greeter = require('./Greeter.js');
document.querySelector("#root").appendChild(greeter());
```

>>>3）greeter：
```javascript
module.exports = function() {
  var greet = document.createElement('div');
  greet.textContent = "Hi there and greetings!";
  return greet;
};
```

>5、做好之后开始打包，cmd里面写

>webpack “填写入口文件的路径，本文中就是上述main.js的路径”（我是空格）“打包文件的存放路径”（不算括号和引号）
eg：

webpack app/main.js public/bundle.js

如果不是全局安装的，这么写：

node_modules/.bin/webpack app/main.js public/bundle.js

这样指定位置就有了打包后的文件了，这里是bundle,js
打开页面看看有没有相应的效果，当然要记得给html引入那个新来的js文件
>6、如果嫌敲命令行麻烦，可以：

>>1）在根目录创建webpack.config.js

>>2）在里面写：

```javascript
module.exports = {
  entry:  __dirname + "/app/main.js",//已多次提及的唯一入口文件
  output: {
    path: __dirname + "/public",//打包后的文件存放的地方
    filename: "bundle.js"//打包后输出文件的文件名
  }
}
```

>>3）跑起来！npm直接webpack就行了，当然如果之前是局部安装webpack的话依然是node_modules/.bin/webpack这么写（些许麻烦）

>7、如果还嫌麻烦……

>>1）打开package.json

>>2）找到“script“，将它设置成："start": "webpack"

（也许么有start，只有test，那就添加进去，不要一激动，把test改成webpack，亲自踩坑）

>>3）这就好了，不管当年你是不是全局安装的webpack，直接npm start就行了思密达

二、思否		路径：https://segmentfault.com/a/1190000013052777?utm_source=tag-newest
-------------------------

>1.创建工作目录；

>2.npm init（创建package.json文件）

>>npm init了之后默认会创建一个项目依赖的package.json文件

>3.npm install webpack --save-dev

>>npm install了之后会安装一些项目依赖的包在node_modules文件夹内。

>4.创建一个静态页（index.html）及入口文件（app.js）

>5.执行命令：webpack app.js bundle.js

>>可以看到执行该命令之后，生成了一个bundle.js文件。

>6.添加模块

>>1.被引用的文件：

>>>module.exports='';

>>2.引用文件：

```javascript
var module = require("./module.js") 
import module from ("./module.js")
```

>7、每次，我们都需要指定两个文件来打包很不方便，并且每次文件有修改需要手动在重新打包也比较崩溃

>>将webpack写入package.json来扩展命令直接用npm webpack即可运行命令

  >>>--watch 自动更新
  
  >>>--progress 显示打包进度
  
  >>>--display-modules 列出打包模块
  
  >>>--display-reasons 列出打包原因
  
  >>>--p 压缩混淆脚本
  

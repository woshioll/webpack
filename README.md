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
#//全局安装
>> npm install -g webpack
#//安装到你的项目目录
>>npm install --save-dev webpack

>npm运行webpack可能会提示需要安装webpack-cli，npm还懂事的询问用户是否自动安装，，，确认yes npm安装，结果一直提升需要安装webpack-cli，然后请教了度娘，webpack版本问题：“在webpack 3中，webpack本身和它的CLI以前都是在同一个包中，但在第4版中，他们已经将两者分开来更好地管理它们。

https://www.jianshu.com/p/826e9c9b9557”

，cnpm全局安装-cli，再-v，如果不行再全局安装下webpack，就ok了

五、运行
-----
 >>* ①、在需要的文件夹中创建一个package.json文件，这是一个标准的npm说明文件，里面蕴含了丰富的信息，包括当前项目的依赖模块，自定义的脚本任务等等。在终端中使用npm init命令可以自动创建这个package.json文件
npm init
输入后会问一些项目详细信息，不准备在npm发布，就一直回车就行
 >>* ②、webpack {entry file} {destination for bundled file}
`# {extry file}`处填写入口文件的路径，本文中就是上述main.js的路径，
`# {destination for bundled file}`处填写打包文件的存放路径
`#` 填写路径的时候不用添加{}


eg：webpack app/main.js public/bundle.js
非全局安装：node_modules/.bin/webpack app/main.js public/bundle.js
参考文章：https://segmentfault.com/a/1190000006178770

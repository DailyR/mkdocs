# Node.js学习笔记

'''
··· Node.js Next.js Vue.js React.js相关知识 —— 部分笔记也放在了有道云笔记上面
'''

### Node.js  5W2H 分析

- 一些基础概念 - 这里仅介绍node 的脚本， 要获取对应的梳理思路，技术map，重新思考的demo

**更多的是注释和使用**


### 主要关注点：

- node和npm安装和实践运行详见下表

[3wschool](https://www.runoob.com/nodejs/nodejs-tutorial.html)

- 无它，唯手熟尔


- 简单的说 Node.js 就是运行在服务端的 JavaScript。

	- Node.js 是一个基于 Chrome JavaScript 运行时建立的一个平台。

	 - Node.js 是一个事件驱动 I/O 服务端 JavaScript 环境，基于 Google 的 V8 引擎，V8 引擎执行 Javascript 的速度非常快，性能非常好。
###

- 用以下命令来查看当前的 Node 版本

```bash
PS D:\Code_Project\git-DailyCode\noot\nootCmd\xIosXcode> node -v
v16.15.1

```

- 使用nodejs除了基础语法的熟悉，大部分可以等到熟悉了框架之后边做边学


### 

- package.json 与 npm的使用

	- 放在nodejs_test2 文件目录下

	- [package掘金上的描述](https://juejin.cn/post/6844903489651343367#%E4%BB%80%E4%B9%88%E6%98%AF-npm)

	- [npm 常见用法](https://blog.csdn.net/weixin_62273462/article/details/121110931)

	- 使用 npm install XXXX(包名) --save 可以对package.json里面的dependecies项目进行修改，同理，使用--save-dev 对应修改的是package.json里面对devDependecies项目

	- [git不提交node_modules文件方法，.gitignore 文件里添加 ](https://blog.csdn.net/m0_61073617/article/details/123926073)

	- 解决了mkdocs_move_files里node_modules和 git上传node_modules过多的问题（工程向）

- 实际工程里引入的第三方包

	- [fastify-w3school](https://www.w3cschool.cn/fastify/fastify-47ju35zi.html)

	- [fastify-官网](https://www.fastify.cn/)

	- [nodemon](https://www.jianshu.com/p/a35dfc72c6e6)

### 客户端使用了nextjs框架，react是个库，nextjs是个框架，基于react的，所以要就直接用next.js就好
- [react](https://www.runoob.com/react/react-tutorial.html)   
	- React 教程
		- React 是一个用于构建用户界面的 JAVASCRIPT 库。
		- React 主要用于构建 UI，很多人认为 React 是 MVC 中的 V（视图）。
		- npm安装react.js
		- react需要V8以上的node才支持，需要先升级node
		- 升级node
		- 到https://nodejs.org/en/下载新版本的 msi 安装包，点击安装，检查node版本

	- 安装 react
		- create-react-app 是来自于 Facebook，通过该命令我们无需配置就能快速构建 React 开发环境。 create-react-app 自动创建的项目是基于 Webpack + ES6 。
		- 执行以下命令创建项目：
```bash
$ npm install -g create-react-app
$ create-react-app my-app
$ cd my-app/
$ npm start
```

- [Next.js](https://www.nextjs.cn/learn/basics/create-nextjs-app)

	- npx create-next-app@lastest 

	- 安装npm-check-updates组件
```bash
npm install -g npm-check-updates
ncu -u
```

- 一般使用git bash来执行，这样能方便地使用到某些unix命令支持

	- [autotest2](../autotest2/README.md) 具体的云真机工程和思路目录

	- [node.js 基础知识](https://nextjs.org/docs)

	- [react.js 基础知识和教程](https://reactjs.org/tutorial/tutorial.html)

	- [next.js](https://www.nextjs.cn/docs/getting-started) 中文版 nextjs教程和笔记

	- 上面的中文笔记相对有点滞后，还是多使用org后缀的英文版吧

	- [我的nextjs笔记,相当于Next.js的分支，也包含基础](NextJS.md)




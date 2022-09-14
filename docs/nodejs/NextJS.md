### NextJS.md


#### 客户端使用了nextjs框架，react是个库，nextjs是个框架，基于react的，所以要就直接用next.js就好（这部分跟README重复，不过是初始部分，重复就重复吧，当做强调）
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


- [nextjs基础](https://nextjs.org/learn/foundations/about-nextjs)

	- To effectively use Next.js, it helps to be familiar with JavaScript, React, and related web development concepts.

	- 捋一下相关概念的关系

	- [ Document Object Model (DOM).]文档对象模型

	- html,css,php -> javascript

	- javascript -> react （node.js npm yarn）

	- react -> next.js  ( fs 库，path库，matter库，node.js 应该插在箭头下面，react到next.js的变化是结合里node.js)


```bash
npx create-next-app@latest  # 我最常用到的新建模板
# or
yarn create next-app
# or
pnpm create next-app
```

- After the installation is complete:

	- Run npm run dev or yarn dev or pnpm dev to start the development server on http://localhost:3000

	- 实测上面的三个命令都是可以用的 2022-09-13 16:16:19 by DailyR

	- 2022-09-09 17:31:38 by DailyR 2022中秋写到这里，中秋后继续学习，学习使人快乐！

	- 2022-09-12 11:06:10 by DailyR 放空了一天，开始重新进入状态。

	- target : finish a demo of next.js

	- 尝试一个next.js里面的各项语法和规则，不怕复杂，就怕没有规律

### 理清各部分的概念后进入实际尝试

- 尝试1：
	
	- 复习基础的html和css和javaScript

	- 本来可以使用wampserver和django的，后来想想方便快捷直接使用在线web站点来运行就好，https://www.runoob.com/try/try.php?filename=try_react_hw  web的形式就是这么简单多样

	- 再后来发现其实直接打开html在chrome浏览器中就行

	- https://www.runoob.com/react/react-tutorial.html 菜鸟教程也包括了一些基本概念concept
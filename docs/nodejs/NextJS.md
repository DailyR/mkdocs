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

	- 捋一下相关概念的关系:

	- [ Document Object Model (DOM).]文档对象模型

	- html,css,php -> javascript     (javascript的分支：jqery，TypeScript，ajax)

		- __一些以前开发的积累经验可以追溯到2014年，2016年的时候（详见百度网盘的flask开发web开发笔记在w网易目录下面的A文章里）__

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


	- 请注意，浏览器无法直接理解 JSX，因此您需要一个 JavaScript 编译器，例如Babel，将您的 JSX 代码转换为常规 JavaScript。

- 什么是 JSX？
	- JSX 是 JavaScript 的语法扩展，它允许您以熟悉的类似 HTML 的语法来描述您的 UI。JSX 的好处在于，除了遵循三个 JSX 规则之外，您无需学习 HTML 和 JavaScript 之外的任何新符号或语法。

	- 请注意，浏览器无法直接理解 JSX，因此您需要一个 JavaScript 编译器，例如Babel，将您的 JSX 代码转换为常规 JavaScript。

	- 将 Babel 添加到您的项目中，要将 Babel 添加到您的项目中，请将以下脚本复制并粘贴到您的index.html文件中：

```html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <!-- Babel Script -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/jsx">
      const app = document.getElementById('app');
      ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app);
    </script>
  </body>
</html>
```

- 上面的就是实际的reactDOM渲染的代码和组件

	- 了解如何通过使用 React 来减少大量重复代码（比javascript代码量精简了很多，也更容易理解）

	- https://beta.reactjs.org/learn/writing-markup-with-jsx


- React 的基本 JavaScript -  JavaScript 和 React 
	> (下文对应例子都是在chrome下面按F12用调试窗口查看)

	- [函数](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions) 例子参考 /nextjs_test/basic_html_css_javascript

	- [箭头函数](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

	- 对象

	- [数组和数组方法](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) 

		- 在/nodejs/nextjs_test/basic_html_css_javascript/javascript_Array_test.html

		- 可以看到对应的例子

	- 解构

	- [模板文字](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)

	- [三元运算符](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)

	- ES 模块和导入/导出语法

```javascript
export const name = 'square';

export function draw(ctx, length, x, y, color) {
  ctx.fillStyle = color;
  ctx.fillRect(x, y, length, length);

  return { length, x, y, color };
}
```

- he first thing you do to get access to module features is export them. This is done using the export statement.The easiest way to use it is to place it in front of any items you want exported out of the module, for example:

	- 要访问模块特性，首先要做的是导出它们。这是使用export语句完成的。例如，使用它最简单的方法是将它放在您希望从模块中导出的任何项的前面

	- 到此，JavaScript的基本基础知识就完成了，实践了一遍，学习实践了

		- 函数，箭头函数，数组和数组方法，模板文字${}, 三元运算符， 模块的到处导入方法 export




#### From JavaScript to React

- 下面继续React的学习

	- 部分React对JavaScript其实是继承的关系，而与此同时也有自己的特色，react是一个库，不是一个框架，next.js是一个框架

	- React 核心概念
		> 要开始构建 React 应用程序，您需要熟悉 React 的三个核心概念。这些是：

		- 组件(components)
		- 属性(props)
		- 状态(state)

	- 在对应的文件中有相应的例子，nodejs/nextjs_test/basic_html_css_javascript/react_jsx_prop_test.html

	- /nodejs/nextjs_test/basic_html_css_javascript/react_jsx_state_hook_test.html  对应的state和hook的例子和理解

	- props属性和 state 状态的区别和联系

	- [useEffect](https://www.cnblogs.com/sexintercourse/p/13740371.html)

		- useEffect使用副作用，监听数值变化，采用对应的处理

#### 接下来from react to NextJs

- 从react.js 到 Next.js

	- [From React to Next.js](https://nextjs.org/learn/foundations/from-react-to-nextjs)

		- I was confused about jsx and javascript for a while in the past, 这是一段我在dev.to留言回复的话，现在明晰了

		- [js和jsx的区别](https://www.cnblogs.com/suihang/p/12089128.html)

		- [JSX看起来像是 JavaScript 和 Html 语言的组合，并柔和在一起，她提倡的是组件化的概念。](https://blog.csdn.net/weixin_39521520/article/details/110748137)

			- jsx就是react 搞出的语法糖
			- 虽然js和jsx在next的pages目录下面运行效果是一样的，但是一般来说不会使用.js
			- 因为在项目中，.js一般认为是可以直接引用的，例如功能库


	- [继续上面的正文](https://nextjs.org/learn/foundations/from-react-to-nextjs/getting-started-with-nextjs)

		- 跳转回index.html文件，可以删除以下代码：

		- react和脚本，react-dom因为您已经使用 NPM 安装了它们。

			- <html>和标签，<body>因为 Next.js 将为您创建这些。

			- app与元素和ReactDom.render()方法交互的代码。

			- 该Babel脚本是因为 Next.js 有一个编译器，可以将 JSX 转换为浏览器可以理解的有效 JavaScript。<script type="text/jsx"></script>标签。

			- 功能React.部分_React.useState(0)

			- 删除上面的行后，添加import { useState } from "react"到文件的顶部。您的代码应如下所示：

			- HTML 文件中剩下的唯一代码是 JSX，因此您可以将文件类型从 更改.html为.js或.jsx.

		- 现在，您还需要做三件事才能完全过渡到 Next.js 应用程序：

			- 将index.js文件移动到一个名为pages（稍后详细介绍）的新文件夹。

			- 将默认导出添加到您的主 React 组件，以帮助 Next.js 区分要呈现为该页面的主组件的组件。


		- 详情可以看nodejs/nextjs_test/basic_html_css_javascript/from_react_to_nextjs_Next_part/pages/index.jsx 这个next.js的实例，pages目录下面的，实际运行有效
		- 至此，完成了一个简单的next.js 单页的应用


#### 接下来讨论next.js的应用实用细节

- Next.js 实战部分
	
	- GOAL： 2022-09-19 16:18:52 by DailyR

		- 利用接下来到国庆期间就是十月一号放假不到两周的时间里面完成这个目标

		- 做一个可以增删改查，有本地存储，有特效的Next.js App应用

	- 时间安排

		- 第一周 ： 9月19-9月23日，完成框架搭建，CRUD，Pages,Router路由

		- 第二周 :  9月26-9月30日，完成复盘，打包，经验总结，做个小程序或者HbuildX的尝试

		- 国庆节前收官，进入10月回来之后一个做项目版本，一个是开始正式人工智能之旅


	- 项目PDCA 

		- P: goal plan budget

		- D: design

		- C: Choeck, Communicate,Clean , Control

		- A: Act, Aim


	- 开始命名为next_navigation

		- npx create-next-app@latest

		- npm run dev 

		- npm run build && npm run start(这个是正式部署，上面是开发环境)

	- cd next_navigation 

		- npm run dev 


### nextjs自身带有服务器，只处理 SSR 渲染。

- 所以需要配合使用 koa2 , store.js, react, fastify 这些库



	- 特别是使用了koa2就像是可以把各种东西集成成为中间件请求一样去处理


	- [React + Next.js + Koa2 开发Github全栈项目](https://zhuanlan.zhihu.com/p/73187063)

	- 虽然 [纯javascript项目也能完成赏心悦目的效果](https://github.com/DailyR/aNavigation)，但是缺乏可以拓展和持续迭代优化的可能（比如利用数据库存储，比如fetch远端数据库数据）

	- Fastify号称是最快的Nodejs 
		- web框架，在Json输出的场景下，通过Json Schema序列化为Json数据

	- Koa
		- Express原班人马打造，定义为下一代Web开发框架。仅提供一个请求上下文，中间件机制，没有捆绑任何中间件。通过利用async/await，让你写出更优雅的代码。方便开发者针对自身需求开发自定义框架。


### next.js 其实可以用很多静态的api

- 在next-navigation 这个测试初始项目里， pages/api 就是用来返回一些静态值方便做测试

	- 例如 pages/api/hello.js 里面的res 返回的json 值

	- axios库搭配使用获取最简单的返回值,意思说可以在api里面处理逻辑

- 当前已完成next-navigation 的 pages下面的 posts 下面的index.jsx和first-post.jsx

	- 而pages下面的api/hello.js可以返回json数据了，详见axios获取api里面的数据

	- [next.js开发实战](https://nextjs-in-action-cn.taonan.lu/#%E8%BF%99%E6%9C%AC%E4%B9%A6%E9%9D%A2%E5%90%91%E7%9A%84%E8%AF%BB%E8%80%85)

	- 做个备份数据吧，axios_test.js

	- 在pages/api/post-rec.js中实验了不同的req.url进行不同的响应函数 if else

- 两个疑问：

	- 1.nextjs中能不能直接使用node.js的语法和模块

	- 2.nextjs中读写文件怎么办

- 回答：

	- 1.可以用，不过要符合import form 的形式，然后指向的path要对应，具体看实例example   pages/post/index.jsx 和 pages/api/post-rec.js 这样就可以实现对应文件的增删改查了，CRUD

	- 2.确实可以直接用nodejs里面的库，只要符合第1条，然后查看[Node API函数](https://nodejs.org/docs/latest-v17.x/api/fs.html#fswritesyncfd-buffer-offset-length-position)


- 完成了文件和axios request请求的实践，完成了最简单的增删改查的需求

	- [next.js 开发实战](../NextJs_Pro.md) 

		- 单篇太长了,就把这篇用来介绍NextJs基本概念和基本操作，新开个next.js开发实战作为笔记好了

		- 有些名字起得太复杂了，文件名，这里稍微规范一下

		- 在page页就使用base，base_advanced_expert_note 这里面的目录文件夹作为一个记录分页

			- 其中base目录就是用来反思基础知识的，要相信写到5000行代码会带来质变效应

			- 有些在pages/posts 目录下面的例子，和在api目录下面的例子，都写得比较潦草，可以在base里面深化优化帮助记忆和思考

			- 像之前提到的前端实战，[next.js开发实战](https://nextjs-in-action-cn.taonan.lu/#%E8%BF%99%E6%9C%AC%E4%B9%A6%E9%9D%A2%E5%90%91%E7%9A%84%E8%AF%BB%E8%80%85)上面提到的这个，可以优先做一个demo试用一下，CRUD工程也好呀

				- 里面提到的技术点：

				- 1.react-query 用来处理请求的

				- 2. next-connect，类似 Express/Koa 这样使用 connect 中间件

					- 修改跨域设置的中间件 cors

				- 3. @hapi/boom 可以在 api route 或者中间件中抛出 Boom 异常

				- 4.Prisma 让你用一个非常简洁易懂的 DSL 语法描述你的数据库结构和表之前的关系，然后自动生成 TypeScript 友好的请求 SDK
					- 这个就是用来ORM ,跟数据库交互的
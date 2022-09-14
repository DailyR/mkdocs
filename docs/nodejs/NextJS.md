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

	- prop属性和 state 状态的区别和联系

	- [useEffect](https://www.cnblogs.com/sexintercourse/p/13740371.html)

		- 使用副作用，监听数值变化，采用对应的处理

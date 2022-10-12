## NextJs_Pro.md

- NextJs_Project 开发实战

	- /nodejs/nextjs_test/next_navigation  项目路径


### 在/nextjs_test/next_navigation/pages/base 路径下开辟基础知识回顾和温习除

- 在各自的/nextjs_test/next_navigation/pages/posts/index.jsx路径下使用注释标签

	- tooltip来直接在网页上面使用浮窗来记录知识点，充分利用html的优势


### 在 /nextjs_test/next_navigation_ts 路径下完成了一个TypeScript的实践项目

- TypeScript 做了个小demo

	- 短期没看到TyperScript的应用场景，实在需要再学也可以

	- 小程序可以用JavaScript来写，其实TypeScript也是通过转换成Js后才运行的，不需要追求新而追新

	- 由于人工智能侧的进展和基础概念的掌握完成，继续回来做react和JavaScript相关的项目了  ——2022-10-11 15:09:28 by DailyR


### [目标:Goal,完成实战](https://nextjs-in-action-cn.taonan.lu/#%E8%BF%99%E6%9C%AC%E4%B9%A6%E9%9D%A2%E5%90%91%E7%9A%84%E8%AF%BB%E8%80%85)

- 拆解，分析


### 前文提要 - 

#### next.js 其实可以用很多静态的api

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

	- [next.js 开发实战](NextJs_Pro.md) 

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

### 完成了上面的koa2和fastify的试用

- 详见/nextjs_test/koa2_test 和 /nextjs_test/fastify_test 的demo

### 回到基础的知识点，继续NextJs_Pro.md

- [next.js 开发实战](https://nextjs-in-action-cn.taonan.lu/#%E8%BF%99%E6%9C%AC%E4%B9%A6%E9%9D%A2%E5%90%91%E7%9A%84%E8%AF%BB%E8%80%85) 


- [继续目标:Goal,完成实战](https://nextjs-in-action-cn.taonan.lu/#%E8%BF%99%E6%9C%AC%E4%B9%A6%E9%9D%A2%E5%90%91%E7%9A%84%E8%AF%BB%E8%80%85)


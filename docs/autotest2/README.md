# AutoTest Platform

'''
··· 自动测试平台
'''

### 拆解自动测试平台的技术要点

- 梳理思路，技术map，重新思考的demo

**更多的是注释和使用**


### 主要关注点：

- [nodejs基础](../nodejs/README.md)

- [STF](Docs/STF.md)

- [scrcpy](Docs/scrcpy.md)

- [ADB](Docs/ADB.md)

- [API规范](Docs/API规范.md)

- [架构](Docs/架构.md)



### 怎么阅读和分析一个node项目？

- 先从package.json 分析用了哪些主流的框架和第三方包，有个大致的了解

- 一些独立功能，比如说console.log这种相当于print,

	- 而类似于express这种类似django的框架，就到工程目录对应的路径里进行npm install express，这样会在当前的文件目录下生成一个node_module目录

	- 然后实际运行的时候就可以使用了，比如在sublime环境下面使用ctrl+B 实际运行（相当于生产环境下的）

- 就架构篇来说，一开始看autotest2的时候会想client客户端是不是用来控制机器的那部分，server就是用来汇总客户端拖的机器的展示给用户实际使用的（一开始的理解，没有形而上学的分类理解就没有进阶的可能，但是只是停留在形而上学的理解就一直不可能得以深入），后来参看项目随着对nodejs的理解的深入发现实际的架构分类不是这样的

	- 真正正确的架构分类

		- Client 客户端用来存放跟用户交互的东西的，无论是component前端用户组件还是pages前端页面，public和stroe 用存放前端静态文件目录和前端公共数据的

		- Design Docs 是产品设计原型和项目相关文档目录

		- Server

			- 服务端用来作为实际的设备控制服务和全局状态服务，自动测试服务这些的，包括@control @state @test base lib utils

		- 看着前端client用了很多像是react nextjs的框架，后端server主要用到的是fastify框架

### 环境准备

- Node.js Version v16.15.1

	- Yarn Node.js 包管理工具

		- 启用，运行`corepack enable`

	- Pm2 Node.js 服务守护运行工具

		- 安装,运行`yarn global add pm2`

- Adb

- Mongodb

- 泛域名https证书，由于设备控制服务前端解码方法须在https环境下才能被启用

- Nginx（设备控制端不需要）


### 服务配置文件介绍

#### 前端配置文件 `Client/config.js`



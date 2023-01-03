# 用来记录一些app技术向开发和变化的思考

### 

- APP 开发

	- React Native

	- 简评4款第三方 React Native 组件库

	- react-native-elements
	- NativeBase
	- react-native-paper
	- react-native-ui-lib

	- 加上美团 beeshell 2.0


- Step by Step

	- npx nrm use taobao  使用淘宝源

	- npx react-native init AwesomeProject 初始化一个叫做AwesomeProject的react-native脚手架项目(一般使用cmd原生，使用git-bash这种第三方容易找不到环境变量)

	- cd "C:\Users\Administrator\AwesomeProject" && npx react-native run-android    运行项目，运行个安卓虚拟机（需要提前配置好环境）


- 2022-11-29 17:40:05 by DailyR

	- 趟了一天的虚拟机AVD的坑之后，新建虚拟机PIXEL5解决问题

	- D:\Code_Project\git-DailyCode\AppOnPhone\ATest\android\app\build\outputs\apk

	- 输出的包在这里，通过飞书互传，在华为手机上验证和启动ok

	- Atest - Demo 项目打包完毕 【Done】

	- 带新包的话，不用把依赖都删掉，只要把 outputs 下面的  apk目录和 log目录删掉就ok了，上一级的,就是跟outputs同级的tmp目录最好也删除掉(前置步骤要打包签名那些)

	- 删除完成之后再在Android Studio下面的terminal 执行 ./gradlew assembleRelease (Project 的Android目录下运行)（运行过程中会把虚拟机连接的node干掉，用上面的npx react-native run-android或者 yarn react-native run-android再开起来就行）

- 到这里，使用React Native打包发布包即可完成了

	- 终于可以往下进行了这样就不会觉得在迷宫里看不到出口而怀疑自己了！

	- Atest项目使命完成，保留不动，验证打包和发布成功

- 使用新项目

	- 初步想还是 

		- demo\Demo （其实大小写都成功，但是为了好看还是弄个大写的了,之后发现大小写不能相同，所以命名成DemoTest）
		- ComponentTest
		- Navigation
		- AwesomeProjectTest

	- 这几个名字

		- 分别的用途到时候再推进具体的，今天用脑太多，要休息一下，明天再继续推进
		- 分别建立了5大目录，用来打包，用来分别实践不同的项目目的，都通过飞书发给华为P40，真机安装测试通过！ 非常重要的里程碑
		- 2022-11-29 17:55:06 by DailyR



- [开始阅读Api文档](https://reactnative.cn/docs/components-and-apis)

	- 启用ComponentTest项目，用来在阅读api的时候对照和实践pratise

	- 测试过程中，如果不符合语法要求会直接弹出红屏警告，这样就能快速定位到出问题的地方了

	- [使用fetch获取数据](https://reactnative.cn/docs/network)

		- 最常用的数据获取，axios也可以在这里用，networking部分

	- [使用导航器跳转页面](https://reactnavigation.org/docs/navigating)

		- 侧边导航栏也在上面这个链接里面，然后一些适配这里面也有说

		- 2022-12-30 16:53:51 by DailyR 梳理了2023年目标，虽迟但到，已完成，详见有道云笔记

		- 2023-01-03 11:29:53 by DailyR 好好说话

- 来自chatGPT的回答
	- react native学习路线
		- 学习 React Native 的路线可能会因人而异，但是大多数人可能会选择以下路线：
		- 了解 React Native 的基本概念，包括它是什么以及它能做什么。
		- 了解 React，这是一种用于构建用户界面的 JavaScript 库。React Native 是建立在 React 之上的，所以学习 React 是学习 React Native 的基础。
		- 安装 React Native 开发环境。这包括安装 Node.js、React Native 命令行工具以及适用于你的操作系统的必要工具。
		- 通过学习 React Native 文档和示例来学习如何使用 React Native 构建应用。
		- 尝试自己创建一个简单的 React Native 应用。
		- 了解如何使用 React Native 开发工具，例如热重载和调试工具，来提高开发效率。
		- 学习如何使用 React Native 的组件和 API 来实现特定的功能。
		- 学习如何在不同的平台上部署 React Native 应用。
		- 尝试使用第三方库或自定义组件扩展应用的功能。
		- 了解如何测试和优化 React Native 应用以提高性能和用户体验。
	- 希望这些建议能帮助你开始学习 React Native！


- 2023-01-03 14:49:54 by DailyR

- 这一步是学习使用控件

	- 已经在ComponentTest这个项目下面使用了Button,View，Text这3个基础控件

	- 事实证明，使用在一级目录路径下的Other.js,移动到base目录下面就可以继续使用了，只要有正确的引用关系声明，例如App.js里面的import * as Other from './base/Other.js'; 
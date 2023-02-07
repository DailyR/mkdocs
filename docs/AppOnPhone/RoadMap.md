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

		- 2023-01-03 11:29:53 by DailyR 好好说话

		- 2023-01-04 09:55:02 by DailyR 知错能改善莫大焉

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

	- 通过navigation.navigate()  —— App.js 里面的进行分页

	- 然后不同业对应不同的base里面的文件来进行例子输出，组件Component的实验和试用
	- 2023-01-04 15:25:58 by DailyR 今日组件，flatlist

	- 2023-01-05 09:43:01 by DailyR  高性能的简单列表组件 flatlist

	- 高性能的分组(section)列表组件  SectionList  这两个例子都已经完成

	- 思考了一下像美团，淘宝这种，其实就是image， text ，button ，底下两个button，加入购物车，立即购买而已，所以实际上根据CRUD,这几个组合已经能完成笔记复杂的应用了，当然还需要很多的实践和尝试来理解里面具体的意思和差别来

- React 基础
	- React Native 的基础是React， 是在 web 端非常流行的开源 UI 框架。要想掌握 React Native，先了解 React 框架本身是非常有帮助的。本文旨在为初学者介绍一些 react 的入门知识。

- 本文主要会探讨以下几个 React 的核心概念：

	- components 组件
	- JSX
	- props 属性
	- state 状态

- 各个Componennt功能都了解了一遍，实例也运行了  2023-01-06 17:51:31 by DailyR
	- 下周计划
	- arguments console.log测试准备

	- console.log确实可以在控制台打印东西

	- [React Native 中文官网文档](https://reactnative.cn/docs/getting-started) 其实可以看到中文和英文都是0.70版本的，所以可以对照着看
	- [React Native Component & API](https://reactnative.cn/docs/components-and-apis)

	- 这两个文档里的中英文控件已经看完 2023-01-09 13:58:32 by DailyR

	- 下个阶段看书本形成体系(即使是印象也可以)

- 2023-01-09 17:02:55 by DailyR

	- 一句话，let和const是var的改良版，能用const就不用let， 能用let就不用var。

	- let,const ,var的区别，var可以重复定义

	-  let，const不可以重复定义 

	-  cosnt必须有初始值，没有初始值会报错

	- let可以没有初始值，后面再声明修改也可以

- JS基本数据类型之symbol  2023-01-11 15:07:13 by DailyR

	- Symbol是一种基本数据类型。Symbol()函数会返回symbol类型的值。该类型具有静态属性和静态方法。
	- 每个从Symbol()返回的symbol值都是唯一的。一个symbol值能作为对象属性的标识符。(https://www.jianshu.com/p/3ac9a471e63d)

- 2023-01-17 14:37:48 by DailyR

	- 年前工作最后一天，面试搞定

	- 一些云原生的知识储备哦，跟优秀的人聊天还上很有价值的，WebAssembly（WASM）

- 2023-01-28 16:27:21 by DailyR
	
	- 开年后工作的第一天，上午完成了内网工作分配和进度推进，下午继续外网的工具开发和知识体系构建

- 2023-01-29 10:45:20 by DailyR 

	- 大胆假设，小心求证

	- 假设const [x，setX] = useState("默认值")

	- 详见 ComponentTest/utils/Text.js  和 ComponentTest/utils/FlatList_Basics.js 里面的刷新的例子

	- 首次在RN下面调通即显示，可喜可贺，今日目标达成！

- 2023-01-30 09:49:22 by DailyR 
	
	- 今日目标是一个利用props进行控件之间的传参

	- 一个是传参完之后进行storage的实验，达成本地重启应用之后数据也不会消失的目标

	- 鉴权可以之后再看，然后到网路fetch获取数据

	- 小知识点：在html里面使用注释可以用这种格式"{/*  */}" 内容

	- 达成了获取textinput

	- 下一步目标 props ，组件的传参

	- 目前ComponentTest/utils/TextInput.js 这个例子里面已经很直观的表现了props的使用

	- 在ComponentTest/utils/FlatList_Basics.js 这个例子里面，重温解决了一个基础概念，这里觉得有必要重点记录一下

		- 首先 [] 中括号这个在 JS里面是表示数组的意思

		- {}大括号表示的是对象

		- 如果存在 [{ key : value },{ key: value}] 这种格式的，就称作数组对象，或者倒过来念也可以，叫对象数组

		- 对于对象数组的一些操作可以详见有道云笔记里的一些网址记录，在【React Native】的一些资料这个笔记里，需要注意的是在js里面 数组是不能直接删除的，要用splice()函数，然后还要用indexof来判断能不能索引到对应的对象，这样才能达成原来需要的删除某个数组对象的目标。而且对于js里面数组的修改和函数使用，它会返回一个修改值，但是原来的Array也是受影响的，所以使用 new Array = array.splice(x,1) 这种表达式，其实会影响两个数组，一个是新数组，一个是旧数组。

		- 注释例子的典范Array_test.js，可以看看里面是怎么复习知识点的 knowledge points


		- 这里要记录下原来的思考过程 2023-02-01 11:06:57 by DailyR

			- 这是一个由陌生到熟悉，大胆假设，小心求证的思考过程，首先明确要解决的问题，就是每个自定义组别里能打印或者说传递参数给某个函数处理，比如像 网站导航的按钮一样，能有自定义的部分

			- 现在看起来，一个是先尝试了<>组件内调用函数给返回值，这样继续在组件内调用这个属性，之后实际尝试发现说行不通到。

			- 在晚上回家的路上，想通了，其实感觉靠谱的应该是声明函数式创建，然后渲染组件的时候采用属性传递参数，然后函数组件根据参数return生成组件，这样就能获取自己想要的东西来，

			- 这样渲染出来的组件就是有自定义的组件了。

		- 重要的是上面的思考过程，对原本不知道不了解的概念和目标想法能小心求证，并且实践求得

		- 编程还是思路的表达


- 2023-02-07 10:27:58 by DailyR

	- 今天开始 TODO list 的构想和设计



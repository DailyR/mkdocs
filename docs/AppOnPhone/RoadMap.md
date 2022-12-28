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

		- 2022-12-26 11:20:04 by DailyR 事实上是用了大半个月才从上线加班和新冠恢复过来

		- 2022-12-27 16:13:22 by DailyR 做好自己能控制的事情

		- 2022-12-28 14:33:44 by DailyR wecenter这种国内试用了一年然后就要收费的，非常不友好，本身也不是什么硬性的指标需要去学习迭代，国内就想着割韭菜，不给长时间的免费和社区版的都不太行

		- 2022-12-28 17:04:14 by DailyR 测试了数据的备份操作，navicat和mysql，wampserver
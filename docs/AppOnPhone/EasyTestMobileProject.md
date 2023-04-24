# EasyTestMobileProject

- 这是一个 EasyTestMobileProject  手机分包下载

	- 这个项目的一个目的是

		- 重温React Native 手机开发的技能

		- 给项目一些测试优化的空间和方向

		- 给自己的流量项目做铺垫，每日可以有所更新 2023-04-23 19:34:06 by DailyR

	- [RoadMap](RoadMap.md) 这个文件里面描述新建一个RN项目的基本步骤

		- 这部分是RoadMap的直接引用复制，

```bash
- Step by Step

	- npx nrm use taobao  使用淘宝源

	- npx react-native init AwesomeProject 初始化一个叫做AwesomeProject的react-native脚手架项目(一般使用cmd原生，使用git-bash这种第三方容易找不到环境变量)

	- cd "C:\Users\Administrator\AwesomeProject" && npx react-native run-android    运行项目，运行个安卓虚拟机（需要提前配置好环境）
```

- AwesomeProject 上面的替换成 EasyTestMobileProject

	- 配置类环境的可以直接用上面这个命令就可以了，如果环境没有配置好，还用重新配置对应的环境

 
- EasyTestMobileProject 的整体思路：    2023-04-23 19:46:05 by DailyR

	- EasyTestMobileProject 先作为React Native的客户端，进行对服务端的数据请求，使用第三方库Axios发起http请求，或者内置的fetch() 函数，向服务器发起Get，post请求

	- 服务端可以用node.js或者 Django里处理http请求

	- 目前暂定用Django（用得最多，最熟悉，其实node.js也不难）

	- 这样子就可以达成每次刷新或者重新打开项目App请求到 web服务器的数据，这样通过web服务器修改增删改查数据，就可以达到通过电脑改数据，而手机端方便收数据的目的了。




- 整体项目拆分大步骤     2023-04-23 19:46:08 by DailyR

	- 新建 EasyTestMobileProject 名字的项目

	- 完成最简单的打包验证

	- 开始客户端请求功能

	- 搭建好服务端进行响应

		- 这一步是电脑模拟器和电脑端服务端直接处理

	- 验证打包装在安卓手机的实际效果

	- 进行细节调整

	- 美化细节

	- 增加专业感

	- 增加各种条件判断

	- 开始日常使用（一周）

		- 开始小组推广试用（）

	- 开始总结经验进行下一个自己的RUB *****



- 2023-04-24 11:03:20 by DailyR

	- cd EasyTestMobileProject && npx react-native run-android    运行项目

	- [目前初始化默认项目使用的是tsx，看起来是从2022年12月开始生效](https://reactnative.dev/docs/typescript#using-javascript-instead-of-typescript)
	
	- [看起来ts替换js是大势所趋](https://blog.csdn.net/shifang07/article/details/105371268/)

	- 
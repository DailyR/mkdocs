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

		- 开始小组推广试用（估计一周吧）

	- 开始总结经验进行下一个自己的RUB *****



- 2023-04-24 11:03:20 by DailyR

	- cd EasyTestMobileProject && npx react-native run-android    运行项目

	- [目前初始化默认项目使用的是tsx，看起来是从2022年12月开始生效](https://reactnative.dev/docs/typescript#using-javascript-instead-of-typescript)
	
	- [看起来ts替换js是大势所趋](https://blog.csdn.net/shifang07/article/details/105371268/)

	- EasyTestMobileProject 这是第一个tsx的react native项目

- 下一步进行打包验证

	- [打包发布中文版](https://reactnative.cn/docs/signed-apk-android)

	- [打包发布英文版](https://reactnative.dev/docs/signed-apk-android)

	- 在对应工程的npm目录下面Android目录下执行了./gradlew assembleRelease 失败
```bash
	- 打新包的话，不用把依赖都删掉，只要把 outputs 下面的  apk目录和 log目录删掉就ok了，上一级的,就是跟outputs同级的tmp目录最好也删除掉(前置步骤要打包签名那些)

	- 删除完成之后再在Android Studio下面的terminal 执行 ./gradlew assembleRelease (Project 的Android目录下运行)（运行过程中会把虚拟机连接的node干掉，用上面的npx react-native run-android或者 yarn react-native run-android再开起来就行）

—— 来源[RoadMap](RoadMap.md)
```

- 第一次构建失败了，查看报错信息在后面增加 --stacktrace 发现是缺少了对应的库包

	- 在stackoverflow查找发现是缺少了对应的库包的缘故

	- 回到工程根目录下面执行npm install安装必要的库包

	- 安装完成之后继续用上面的./gradlew assembleRelease命令尝试

	- ./gradlew bundleRelease 这个命令是生成发行用的abb包（就是以前的apk）
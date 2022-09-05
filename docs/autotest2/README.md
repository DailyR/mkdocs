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

	
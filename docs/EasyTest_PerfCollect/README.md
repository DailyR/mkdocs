# EasyTest_PerCollect

'''
··· EasyTest_PerCollect  一个性能收集平台
'''

### EasyTest_PerCollect  

- 全称为 EasyTest Performace Collect Platform

- 正式命名  EasyTest Perf Collecting Platform

- 昵称 EasyTest Cloud Perfmance Platform

**EasyTest性能收集平台**


### 基本开发和发布规则：

- 内网ip:8000 为正式发布端口

- 8001 ,8002为测试端口  使用temp_demo

- 无它，唯手熟尔


- 外网ip:8001 为正式发布端口

- 外网这个也兼职了测试调试，因为用的人暂时频率不高，所以可以在正式环境调试

### bootstrap和echart时隔这么久之后，大概5，6年之后重新用起了echart

- 宝刀未老

- 一些思考

	- echart升级到了 5.4.0 版本，应该说还是相当与时俱进的，能从时代中竞争活下来确实是很了不起，还能持续进步

	- bootstrap也升级到了5版本，相比之下基于boostrap 3,4的flatlab，flatUI，已经很久没有更新了，这点颇为遗憾，

	- 所以左思右想之下，虽然dynamic table是 flatlab对boostrap之前老版本的封装更实用，但是没有之后升级的新特性和快感，也没有维护了，想想，基于目前的需求其实还是


### 一些独立功能和模块思考

- 一些独立功能，比如文件遍历功能，这些在navigation的工程下面是以函数形式存在，这些大部分是可以直接拿来用的
	
	- 例如在django html 页面展示数据，传值views下的render接口

	- render接口传字典，字典里可以是dict，可以是list或者set,但是首先它是个字典

	- 然后注意点是echart里面的M需要去除，echart只能渲染数字形式的数字或者字符串


### 将一些之前的思考顺序记录下来不然过段时间就忘记了  2022-10-20 15:57:47 by DailyR

- 1.选择 echart line视图，bar视图，构建sample， example

- 2.传内网，保持持续动力

- 3.思考页面，是否引入db管理 model

- 4.解析parse数据和template展示

- 5.简单的route展示



### 当前目标：route页 展示美化

- bootstrap5 版本看着展示比3，4更符合现代人的审美 2022-10-20 16:01:07 by DailyR

- 决定使用最新版bootstrap5

- 最终下载版本是[bootstrap-5.1.3-dist](https://v5.bootcss.com/docs/getting-started/download/)

### 基础

- [纲领基础](base_advanced_expert_note/README.md)

- [基础练手](base_the_hard_way/README.md)

- [功能小试与备忘](advanced-lessons/README.md)

- [开发字典](kubernetes/minikube/dictionary.md)

- [常用变量命名](https://segmentfault.com/a/1190000015638398/) Var_Standard_Python自己也写了一些,或者直接点击链接里也有介绍一些name-typing

- [59个具体都书写更优质python代码的方法](59_Specific_Ways_to_Write_Better_Python.md)

	- 在书写的同时，可以用flake8和pylint 来检查书写规则，规范书写能让整个文档的可读性变得更强，更舒服。


### 其他一些小记

> - auto_reload 用来做开发调试的重载，不用每次都运行执行（用来小规模的开发调试非常方便）

> - unity打包环境，gradle打包

>> - 工程化思维

#### 很多时候其实是积累的力量，量变引起的质变

- 走了很远，但是别忘记自己出发时候的样子

	- 知乎上面一堆laodmap学习路线图，但是感觉学与用严重脱节，而且都是类似培训班似都东一点西一点，还不如自己慢慢查资料和看书，总比被误导都强。

	- 编程的自信程度，介于高手和大牛之间吧，还达不到大神都程度，但是算菜鸟和入门也不至于，经常练习，经受岁月的洗礼，提升自己解决问题的能力和思维就是对自己最大的肯定，相信自己。
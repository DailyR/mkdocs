# EasyTest_PerCollect

'''
··· EasyTest_PerCollect  一个性能收集平台
'''

### EasyTest_PerCollect  

- 全称为 EasyTest Performace Collect Platform

**EasyTest性能收集平台**


### 基本开发和发布规则：

- 内网ip:8000 为正式发布端口

- 8001 ,8002为测试端口  使用temp_demo

- 无它，唯手熟尔


- 外网ip:8001 为正式发布端口

- 外网这个也兼职了测试调试，因为用的人暂时频率不高，所以可以在正式环境调试

###

- 加了些 lua ， vbs 的使用例子，由于文件较少，就不单独开立项目了，合并在一处，方便查看

- 一些独立功能，比如svn版本获取，文件遍历功能，这些在navigation的工程下面是以函数形式存在，这些大部分是可以直接拿来用的
	
	- 在advanceed里面有细分的小模块，工程化思维的构建，一些process的认知，在EasyTest各个版本的路径下面的sample文件夹里也有不少的demo和sample例子

- 隔一段时间再编程的话最好有时间可以再练练基础


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
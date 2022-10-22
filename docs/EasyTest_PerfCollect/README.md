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
	
	- 看半天没找到bootstrap分页的好例子，最后找的了django自己实现的分页功能，简单易懂（完成得很漂亮 2022-10-22 14:06:14 by DailyR）


### 当前目标：route页 展示美化

- bootstrap5 版本看着展示比3，4更符合现代人的审美 2022-10-20 16:01:07 by DailyR

- 决定使用最新版bootstrap5

- 最终下载版本是[bootstrap-5.1.3-dist](https://v5.bootcss.com/docs/getting-started/download/)

### 一些小技巧

- 利用选中的代码，在sublime里面 快捷键 ctrl + shift + / 就可以快速注释了


### 已于昨天公告上线 2022-10-22 11:01:31 by DailyR

- 目前看好评还不错

	- 准备进一步做营销和推广

	- 积极写文档总结，抽象出经验和模板模式来

- 大概下一步还会有一些小的更新和尝试

	- 加入django Model来管理文件，现在直接放在文件夹里数据量不大的时候满足base需求，数据量大的时候可能就不那么美好了


### 阶段性总结

- 重新温习了django
	- django-admin startproject myproject 开始一个新的项目

	- python manage.py startapp myapp 新建一个app（就是在项目里添加对应的文件夹目录模板脚手架）

	- 还不要忘记在setting中添加对应的配置修改


- 思考过程

	- 先启动了django post 去接收和存档一个文件，详见upload_app

	- 因为想着不跟主目录混淆所以用的upload_app，最重要的是from django.forms import forms 这个专门用来接收文件的类，中间有些小问题但是最后调通了，这样就完成了数据文件的获取

	- 然后templates ，static 这些引入是为了echart 和 bootstrap来做准备的。

#### 很多时候其实是积累的力量，量变引起的质变

- 走了很远，但是别忘记自己出发时候的样子

	- 知乎上面一堆laodmap学习路线图，但是感觉学与用严重脱节，而且都是类似培训班似都东一点西一点，还不如自己慢慢查资料和看书，总比被误导都强。

	- 编程的自信程度，介于高手和大牛之间吧，还达不到大神都程度，但是算菜鸟和入门也不至于，经常练习，经受岁月的洗礼，提升自己解决问题的能力和思维就是对自己最大的肯定，相信自己。
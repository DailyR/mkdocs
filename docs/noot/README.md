# xPackage

'''
··· coding by myself
'''

### 拆解打包机的一些学习经验和笔记


- 主流思路：
	
	- 学习编程语言和学习人类自然语言并无二致。小时候我们开始说话的时候都是从模仿开始的，而且就只能发出最简单最容易发出的声音（爸爸或妈妈），但是当大人不断的教给你新的词汇，随着你的积累和练习越来越多，这个时候你就能随心所欲的表达自己。学习编程语言也是如此，在最开始的时候，你的能力只能驾驭“hello, world”这样的代码，但是随着学习和积累，总有一个时候你可以随心所欲的写自己想写的代码，控制计算机做我们想让它做的事情。当然，这里需要一个顿悟的过程，顿悟显然是一个从量变到质变的过程，顿悟的快慢应该取决于量的积累，也就是相关知识的积累。当然，如果你要成为改造世界的天才程序员，这个估计天分还是至关重要的因素，就像天才是百分之一的灵感加上百分之九十九的汗水，但百分之一的灵感起决定性作用。但是对于普通人来说，编程学不好还真不是天分的问题，那多半是因为量的积累还不够，这里的量一方面是新知识的汲取，一方面是旧知识的巩固。



- 抓住类继承框架的思路

	- 任何工程都是思想思路的逻辑表达
	- 都是一场自圆其说的工程拆解，print ,type ，dir 少不了

- 需要有一个最小拆解环境，demo,workspaces

	- 很多驱动来源于状态的改变，而监控不同的condition
	- 可以通过不同的file修改来解决，类似于移动到不同的目录文件夹
	- 类似于将文件名命名为不同的标准格式，例如后面带.ok, .error
	- CLI是很重要的衔接不同的编程模块和功能的工具
	- 然后在文件里面填充不同的文本，也可以达成目标
	- 例如，noot打包框架就是通过php的js，修改对应目录下的文件
	- 再通过python框架命令，监听到不同目录（代表不同状态）的任务，然后读取文件内的json数据信息参数，进行的不同的构建
		- 核心Key就是读取文件json，进行分类，写入了json


- 使用admin__.php 来进行对应的js修改
	
	- 然后DataFlow RoadMap(Route)到对应的类进行xPackage打包
	- 这一套项目用了很多年，确实有其独到之处，能经历得起时间考验的才是经典项目。


- 通过这个项目的拆解，想到了几个可以写的idea
	
	1. 在wampserver上面的对应目录挂不同人的名字，然后进行文本文件的修改，这样可以达到每天日报的汇总。后端起一个python来监控处理对应的文本文件（比如说挪位置，或者读取后插入数据库进行删除就好了。）
	2. 其实从原理上也可以直接连接和修改数据库进行这个每天日报汇总。
	3. 因为对应的webhook是可用的，那么自动提醒又可以用popo机器人日报提醒那一套了，看要不要复用而已。（这个跟1,2不是同一个功能项目）

- 打包机逻辑

	- 拆解功能

	- 可复用功能和思考模式 - 见下面的

	- 调试可以使用autoreload的模式进行运行，对应目录文件在/auto_relaod/test_reload.py 可以查看(可以在sublime的左侧文件夹栏进行右键点击对应的文件，进行复制为选择文件路径操作)

	- noot/nootMain.py 用于项目的主路径进入，涉及的知识点是接收解析系统的传参 sys.argv ,通过接收不同的参数从而启动不同的服务类型进行服务（一般思考可以从这个思路作为切入点，因为之前airtest的testcase似乎也是这样组织的，然后CLI可以很灵活适配各种方式）

	- [base_expert_note](../base_advanced_expert_note/README.md)


	- 启动用的runner, 详见/noot/nootCmd/runner/RunnerCmd.py  文件

	- RunnerCmd.py内网阅读理解到此处，这个是作为一个监督线程来进行处理的

		- 监督过程先看对文件夹的监管

		- fileUtil包括了常规到文件夹和文件操作，新建删除等，clearFolder这些

		- RunnerCmd.py 79行，进行的是pop处理需要处理的文件

		- 接下来进行runningFile和可只执行参数的实际拼接

		- 这里是每个派发的实际执行处

### 打包机实机拆解例子

- 启动

	- nootMain.py

		- 此处为框架启动的入口

```CMD
@pyhton3 C:\nooot\jzxx\noonMain.py runner -baseFolder "C:\wamp64\www\build\jzxx\task" -sleepTime "8"
```

		- 参数

			- argv 

				- {'baseFolder':"C:\\wamp64\\www\\build\\jzxx\\task","sleepTime":"9"}

				- package_name 

					- runner

	- cmdUtil.py 

		- 执行对应命令的入口

```python

className = packageName[0].upper() +packageName[1:]  + 'Cmd' 
print("className")
print(className)
targetClass = eval(className)
print(targetClass,targetClass.__doc__)

print('')
print('='*10 ,'[start]',packageName,targetClass.__doc__.strip(),'='*40)
print('')
cmd = targetClass(argv)
executeResult = cmd.execute()

```


- 任务执行

	- RunnerCmd.py

		- 定时查询需要执行的任务

			- 
```python
def __executeWaiting(self, waitingFolder, runningFolder, finishedFolder,scheduleFolder):
	'''执行waiting的内容'''
```
			- 管理所有的任务

				- waiting 

				- running

				- finished

				- schedule
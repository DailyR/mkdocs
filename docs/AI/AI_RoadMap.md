# AI RoadMap 

- [My ControlNet Project](https://github.com/DailyR/ControlNet)

	- 一些基本资料和项目


- [style2paints](https://github.com/DailyR/style2paints)

	- 给样式图上色


-  一些思考 2023-03-18 17:06:52 by DailyR


- 路径的修改


- 题外话，tree的使用

	- 使用tree命令生成树形结构
		- tree 命令的使用：-> tree --help不记得的时候就使用一下帮助，看一下说明， tree -d 就是列列表， -L 2 就是最多只列两层路径

	- 后来发现： 用git-bash 里面的tree 命令更快，不用跳来跳去看路径问题

```bash
$ tree -d -L 2
.
├── 0.Math
│   ├── 0.basic
│   └── 1.CS229
├── 1.python-basic
│   ├── Python-100
│   └── images
├── 2.numpy
│   ├── images
│   ├── numpy-100
│   └── numpy_exercises
├── 3.pandas
│   ├── 1.10-Minutes-to-pandas
│   ├── 2.Pandas_Exercises
│   ├── 3.pandas_beginner
│   └── 4.Pandas50
├── 4.scipy
├── 5.data-visualization
│   ├── 1.matplotlib
│   └── 2.seaborn
├── 6.scikit-learn
│   ├── data
│   └── solutions
├── 7.machine-learning
├── 8.deep-learning
│   ├── Deep-Learning-Papers-Reading-Roadmap
│   ├── PyTorch_beginner
│   └── word2vec
└── 9.feature-engineering
    ├── FeatureSelectorUsage
    ├── data
    └── images

31 directories
```

- 可以看到当前的AI目录是去年22年10月份左右做的目录路径，大部分是lession说明概念的

	- 现在要改变目录结构，把ControlNet和Stable Diffusionzz类似的AI项目也包括进去。

```bash

$ tree -d -L 2
.
├── lessons
│   ├── 0.Math
│   ├── 1.python-basic
│   ├── 2.numpy
│   ├── 3.pandas
│   ├── 4.scipy
│   ├── 5.data-visualization
│   ├── 6.scikit-learn
│   ├── 7.machine-learning
│   ├── 8.deep-learning
│   └── 9.feature-engineering
└── projects
    └── ControlNet

```

- 这样改造的目录比之前直观些，然后ControlNet纯代码，不包括训练集的话（各种pth文件），其实并不大，大概90多，快100M 这样，比很多软件都要小了。

- [Dictionary](Dictionary.md) 



### 这里添加一段自己的感想

- 好多时候，不轻易放弃，不断琢磨想办法，这个就是个人能获取成就感和比昨天的自己更进一步的地方：

	- 之前好几次遇到类似的情况，比如在做APP开发的时候（详见/AppOnPhone/README.md，难点主要在配置各种Android开发环境包括虚拟机和打包环境），比如在erl远程包一层进行调用但是传入函数无法执行的时候（详见erlang_Code/RoadMap.md），如果过早的放弃，就不会有自己现在比较好用的TODO LIST APP, 同理到erl的调试，如果过早的放弃，就不会有能远程调用erl, 进行战斗回归功能测试的套件和入口；同理到了AI开发的这个实验，如果因为没有显卡就放弃了，如果因为内网没有联网就放弃了，就没有后面那么多能激动人心的训练画图了。

	- 想尽一切办法，不要轻易放弃 。 ——  2023-03-20 14:29:04 by DailyR

### 设立新的目标

- 短期可以给项目上线让路，像去年4，5月份末日一样

	- 短时间来说，像AI的认知可以持续被刷新，“未来职场只有两种人，一种上会使用AI的人，一种是创造AI的人。—— 疑似任正非说的” 即使不是任正非说的，也是很有道理的，对信息处理行业的岗位可替代性冲击很大的，打不过就加入，这是一种减少内耗的方式。

		- 而且AI也替代不了专业度足够深的人，只有足够深的专业度，才能判断产生的信息是对是错，有足够的能力判断对错

		- AI chatGPT立下的一个功劳，加深了bash和bat的快速理解和实践使用，详见有道云笔记，可以调用自动化测试机器人了

	- 配置好了Intellij IDEA的环境，这样代码跳转和自动补全就都搞定了，方便的看erl代码。详细可以看有道云笔记，主要就是新版本的Intellij IDEA,然后安装对应版本的erl插件就好了。


	- GM指令的文档也可以告一段落了，已经想清楚怎么整理了


- 2023-04-20 15:31:05 by DailyR 时隔1个月左右

	- 经过这段时间疯狂加班，导致个人向的一个开发停顿了许久

	- 需要重新出发的话需要考虑最重要的需求

	- 经过了几天的休息（适度休息，也不能太闲，太闲容易进入转态慢）考虑还是要通过项目来进行对应的开发需求。
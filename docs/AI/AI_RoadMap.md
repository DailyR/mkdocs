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
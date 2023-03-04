# Erlang_Code

'''
 coding just for fun by myself to understand erlang
'''

### 一些erlang的实例还有基本概念

**更多的是注释和使用**

···
- Erlang Code 相关
- 解决问题的能力
- 无它，唯手熟尔
'''

###

- 2023-02-27 10:43:19 by DailyR

    - 从上一个APP开发的工程目录 AppOnPhone/ComponentTest ，切换到这里，其中最大的想法是从 AppOnPhone/README.md - 2023-02-27 09:54:04 by DailyR这段可以得出，此处是从新的初心三选一项目里面选了一个最贴近项目实际的第一个初心项目进行推进

    - 这个项目的初步想法是推进建设平台化能力

        - 用cmd 从 python 调用erl的能力，从而调用到当前环境下的机器人，从而思考测试用例

        - 所以要花点时间完成一下预研工作
            - 其中包括，1. 使用Erlang的版本，和文件组成工作形式

    - 当前的路径及目录格式为
```bash
├─doc
├─erl_script
│  └─gs
│      ├─config
│      └─src
├─src
├─system
└─tools
```

- 增加一个tools目录用来存放erl版本数据

    - 2023-02-27 11:03:34 by DailyR
    - 第一步，先确认erl的环境和版本，使用的是要尽量跟项目当前的erlang版本对齐的环境。
    - doc目录用来放一些学习资料， 或者cookbook 手册之类的
    

- 一些安装环境和文件

    - [Erlang官网下载](https://www.erlang.org/downloads)
    - [一个LoadMap](RoadMap.md) 
    - 目前内网项目相关的版本用的erl 23.2, 详见上一行RoadMap里面的解释。




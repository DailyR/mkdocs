# Erlang RoadMap 


- [w3c School 的erl](https://www.w3cschool.cn/erlang/)

	- 一些资料的准备

- 初始环境的问题

	- 一般服务端erlang的调试需要下面这些东西

	- 1.IntelliJ IDEA用来打开后端工程

	- 2.CMD或者CygWIn 这个用于代码的热更新，或者其他一些基础的命令行操作Operate

	- 3.Py- Sublime Text环境，用于尝试启用某些py脚本

- 一些安装环境和文件

    - [Erlang官网下载](https://www.erlang.org/downloads)
    - [一个LoadMap](RoadMap.md) 
    - 目前内网项目相关的版本用的erl 23.2, 因为下载选项不是特别明显，选了一个 erl 23.3 版本，放在了tools目录下，选择默认安装环境，然后添加环境变量即可，在命令行直接erl，有命令行解释器版本 Eshell即是安装成功。

    - 后来发现tools目录不能放超过 github  100M 大文件的限制，所以改为放在本地其他地方，百度网盘litteTools路径下也存了一个，然后tools目录下就放一个带版本号名字的空txt，这样就可以上版本号的就记录下来了。 （发现快捷方式如果要上传的话，会自动检测源文件，超过大小限制也会报错。）

- 2023-02-28 17:09:48 by DailyR

	- 完成了一个远程cmd调用执行 erlang 服务器 多部队战斗的场景

- 2023-03-01 17:01:32 by DailyR

	- 二月结束，三月依始，开始做远程erlang的一些调试和试用

	- 调用了一些机器人接口

```bash
用于调用erlang 命令


cmd   使用   bash -c  就相当于 cygwin bash直接执行啦。
在内网成功执行了cmd来对游戏进行影响
可以正常运行的cmd，  需要在有beam的目录下执行
bash -c "erl -name tmp@localhost -hidden -noinput -pa ebin/game -setcookie node-cookie -s game_ctl extra game_4399_s8@172.18.40.79 eval 'db:count(role)'"

可以正常运行的cmd，这个的目的就是在开启robot节点的情况下，在根目录下的ebi\game 路径目录下面执行，
在机器人节点下执行的 机器人模板初始化
bash -c "erl -name tmp@localhost -hidden -noinput -pa ebin/game -setcookie node-cookie -s robot_ctl extra robot_app_4399_s8@172.18.40.79 eval 'rm:init_troops_data(60,[[1,2,3],[4,5,6],[21,23,24],[25,26,41,[42,43,44],[81,83,91]]).'"

开个EXE账号去  2034,，1737 观察坐标

%% 执行正常， spawn 的写法也是可以的，但是String里面如果带有函数，
%% 就要在 fun -> 箭头增加双引号 ">"  ， 这里初步估计是跟cmd下面的特殊字符串有关系， > 需要增加两个引号
bash -c "erl -name tmp@localhost -hidden -noinput -pa ebin/game -setcookie node-cookie -s game_ctl extra game_4399_s8@172.18.40.79 eval \"serv_ets_handler:cast({func,fun()-">"test_troop:loop_check(5,'robot_app_4399_s8@172.18.40.79') end}).\""

(Ps:一些可以补充的前置条件，比如需要robot节点打开，执行时候需要经常看机器人节点的表现
Pss: 本质是利用erl的同局域网下的node节点 cluster 集群特性来进行 远程注入执行的，这样就像websocket一样达成远程通信的目的，目标)
```

- 2023-03-04 14:21:01 by DailyR

	- erlang基础

	- 新起一个技术点文档，这样在做笔记的时候就可以用 [Base_Knowledge_point](Base_Knowledge_point.md)
	
-  对于通常意义来说 2023-03-06 10:42:56 by DailyR
 
	- 如果我们要学习一个语言，最先学习的是各种print，或者说log

	- 然后是各种基础逻辑预防，if...else， while什么的

	- 程序 = 数据结构 + 算法，这个法则在计算机编程领域还是一直比较通用的，

		- 详细一点就是数据结构 ，数组， list列表这些要怎么表达

		- Str，number ,To String ，To number

	- 然后再到各种语法糖和特性

	- 学习资料一般说 w3c 的主要是术的层面，而 官方文档的主要是 道的层面，术与道相结合吧

- erlang运行环境的问题 2023-03-06 15:11:10 by DailyR

	- 详见factorial.erl
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
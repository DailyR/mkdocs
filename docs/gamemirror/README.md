# DailysCodeDocs

## coding just for gamemirrot


###  


**更多的是注释和使用**


···

### gamemirror主流程

'''
- 将 win32窗体嵌入 pyqt5中

- gamemirror是起了一个 websocket 来进行rpc连接

- 其他较好的工程project级别的习惯，把UI相关的设置抽象成了一个类，来引入启动模块，这样会显得非常有条理

'''

**win_gui相关模块**

###

- 详见PyQt5的开发
- 一些独立功能，比如svn版本获取，文件遍历功能，这些在navigation的工程下面是以函数形式存在，这些大部分是可以直接拿来用的
- 还有一些比如robot机器人和protobuff的使用，可以详见stress_robot项目
- python-crontab 可以提供定时接口

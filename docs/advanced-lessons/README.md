
# 进阶python

'''
这里是一些实用例子
'''


- SysArg.py 主要列举的是系统参数传参进来的例子， 例如 cmd 执行 python SysArg.py 时，就可以  python SysArg.py Hello, 这样sys.argv[1] 就能捕获这个传给程序的参数,从而增强程序的灵活性，获取不同的启动和运行参数

- Alert-sysArg.py 功能是配合windows系统的任务计划程序可以设置很方便的提醒, pyinstaller -F XXX.py  可以获取 exe , 在此基础上 设置任务计划，每小时调用一次，对 exe 传入参数  每小时提醒   起来走一走，喝口水  可以设置非常实用的提醒器, 小而美
	- 可以看到sys.argv是不需要预先在代码块里设置的，因为是实际CLI调用传进去的时候默认接收的

- MySQLdb记录的是MySQLdb模块的使用， MySQLdb 最多只支持到 python3.4 ，一般都是用在python2里面 ,python3 用 pymysql了

- pymysql 里在python 写了个 pymysql的例子，可以用于django的 CRUD，例子是excel表目录里的excel存储和查找，至于在django中 ，直接用pymysq快还是 models处理更快，还有待实验，不过ms级的快速响应还是比较舒适的。


- missing_method_getattr.py 
	- 记录反射特性，我们可以理解为，通过访问字符串的方式，访问到了字符串的变量值(而一般情况下，访问字符串，就返回字符串本身)。这就是反射最明显的特征。反射reflection，指运行时获取类型定义的信息。一个对象能够在运行时，如同照镜子一样，反射出其类型信息。简单而言，在Python中，能够通过一个对象，找出其type、class、attribute或者method的能力，称为反射或者自省。

- FileConfig_Get 这个目录
	- 主要是一些工程的项目，比如Config，ini的这种格式的获取和解析，也挺多的那种根据json或者xml来解析的，不过工程里方便配置的还是这种config和ini的格式的吧，在自己的项目里面，EasyTest就用的这个形式来获取配置的

	- 很多时候我们的工程和项目规模还用不到DB数据库，那么用文件来读取或者存取一些关键数据或者结果或者过程数据就会显得比较重要

	- 其实在File可以成为一个对象单独操作，只要有对应的赋值，然后毕竟DailyCode这个项目是自己的练手和笔记note型项目，那么有些零散的笔记和知识点难免重复，可以在备注里归类到一起。

	- 多加描述性语言也很重要

- /advanced-lessons/os_path_file_test.py
	
	- 这个主要是文件及相关路径，在os.path上面的应用，对于大多数情况下，文件相关的，直接看这个文件和例子就可以了。

	- 里面相关的4个文件及主要实例都已经写在里面了

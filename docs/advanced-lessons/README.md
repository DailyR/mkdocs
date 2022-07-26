
# 进阶python

'''
这里是一些实用例子
'''


- SysArg.py 主要列举的是系统参数传参进来的例子， 例如 cmd 执行 python SysArg.py 时，就可以  python SysArg.py Hello, 这样sys.argv[1] 就能捕获这个传给程序的参数,从而增强程序的灵活性，获取不同的启动和运行参数

- Alert-sysArg.py 功能是配合windows系统的任务计划程序可以设置很方便的提醒, pyinstaller -F XXX.py  可以获取 exe , 在此基础上 设置任务计划，每小时调用一次，对 exe 传入参数  每小时提醒   起来走一走，喝口水  可以设置非常实用的提醒器, 小而美

- MySQLdb记录的是MySQLdb模块的使用， MySQLdb 最多只支持到 python3.4 ，一般都是用在python2里面 ,python3 用 pymysql了

- pymysql 里在python 写了个 pymysql的例子，可以用于django的 CRUD，例子是excel表目录里的excel存储和查找，至于在django中 ，直接用pymysq快还是 models处理更快，还有待实验，不过ms级的快速响应还是比较舒适的。


- missing_method_getattr.py 记录反射特性，我们可以理解为，通过访问字符串的方式，访问到了字符串的变量值(而一般情况下，访问字符串，就返回字符串本身)。这就是反射最明显的特征。反射reflection，指运行时获取类型定义的信息。一个对象能够在运行时，如同照镜子一样，反射出其类型信息。简单而言，在Python中，能够通过一个对象，找出其type、class、attribute或者method的能力，称为反射或者自省。


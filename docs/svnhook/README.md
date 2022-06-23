# svnhook

'''
··· 对应的svn hook检察需求隔了几年时不时就会冒出来，操作步骤总是好记性不如烂笔头，索性这次一起记录下完成的过程
'''

### 方法论：


**更多的是如何分析和使用**


### 主要步骤：

- 1. 确定主题： 如 svnhook  【DONE】

- 2. 主题分析： 步骤分解： 【DONE】
	
	- 获取资源，百度云，有道云，（网上零散资料的重新组装和实践）

	- 搭建svn服务器

	- 放shell脚本，py脚本，生效条件检查

	- 服务器端口防火墙检查

- 3. 实践提交脚本 【DONE】

	- 对应的问题的总结，pre-commit 需要 chmod 755 xxx对应脚本

- 4. 内网同步外网 【DONE】



### 对以上步骤的解析：

- 对应的文件放在hooks目录下，这个是svn server创建好对应的svn 服务端就会自动创建的一个目录
	
	- 里面的文件包括pre-commit.tmpl, 这样的以tmpl后缀名结尾的名字，这个本身的是一个shell脚本

	- 如果想要使得这些脚本生效，就把tmpl后缀名去掉就好

	- 通过shell来调用对应的python脚本进行检查会比较方便，毕竟自己最熟悉的语言还是python

- 参考链接汇总
	
	- 《使用Python写服务器端的SVN Hook》 https://www.jianshu.com/p/2596c9d2d4d3

	- 《svn添加强制注释，pre-commit结合python》 https://www.cnblogs.com/younldeace/articles/5179668.html

	- 《常用命令之svnlook命令》 https://blog.csdn.net/carefree2005/article/details/122947419

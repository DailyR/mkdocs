



--------------------------
文件说明
--------------------------

- 这里是websocket的例子
	- websocket的概念不再详述，简单概况就是可以web端和pc端都使用来做全双工通信
	- django_websocket_server_test.py 就是起的django asgi websocket 服务器
	- django_websocket_client_test.py 就是 websocket_client_test.py 换了个端口

	- websocket_server_test.py 这两个是一对，原生的websocket直接测试
	- websocket_cleint_test.py 
	
	- 运行一下就能理解了，注意点可以看这几个文件里的注释
	- 基本上对websocket可以有个比较实在的理解

	- 详见 Websocket试用里程碑.png 结果


- websocket_server_sample1的例子是基于websocket_server_test来改造的
- 跟djangoweb的区别在于django_web还没掌握从服务端发送消息给客户端的能力，而websocket_server_sample1已经掌握了，这个后续可以再深化和拓展


# Robot压测机器人

## stress_robot 压力测试机器人 


###  stress_robot framework


**基本思路：  使用 threading.Thread 创建多线程机器人， 获取登录信息，然后启动守护进程，利用协议解析，protobuff对服务端进行收发通讯**


···
- 使用 pykka 做状态管理，

- 入口在main.py 具体看注释

-  case 在 case.py    用工具拿协议  ，protobuff 解析协议详见 protobuff目录相关的例子，在robot里面的runCase里面调用，用反射方法生成实例，
如果要不停发，就另外开一个线程，给个join(time), 不然其他线程就会阻塞
'''


### 大致流程

- 先去服务端的某个url获取 token，然后完成登录逻辑，收到的信息再做各种行为操作

- 每个线程相当于一个玩家，模拟玩家协议客户端，所以通过实现客户端协议和调用服务端协议，就能实现任何想要的功能


### 每个文件夹的作用

- Case 用例

- common  登录信息等，主要是获取token之类的

- Des 序列化协议方法

- Logs 日志打点

- protoBuff  存放protobuff的地方，可以写bat,shell来对 .proto 生成  pb.py 文件

- robot 机器人逻辑 


## send_pack_recv_data_from_server_sample  单个协议机器人例子

### send_packet_and_recv_data_from_server.py  是一个自己构造socket完成， packet 发包给服务器的实际例子，在内网已经调通

- 用socket 自己构造一个packet 包发送给serv请求， struct pack，unpack ,    to_bytes()   , protobuff

- 实例就是一个激活包，然后再发送一个心跳包，获取服务器的返回心跳包，然后用protobuff进行解释，能获取的到解析的正确内容

- 本例子完成： （slg- lowpoly项目）

- 常见的arpg服务器是用tcp连接的，高实时的喜欢用udp，一般还是用tcp较多

- 基础解析：

- c2s : 4字节包长+2字节UniqSeq+2字节协议号+协议内容

- s2c : 4字节包长+2字节协议号+协议内容(跟c2s的包的区别主要就是少了自增的UniqSeq)

- OutPut 如下， 那么此时此刻，所有的压测构建和基础例子就行得通了，（粘包处理用pykka那些后续再处理）

- 其中，协议内容是用的protobuff 解析生成的， bytes字节流， 其他不是protobuff, 其他是struct 和 to_bytes() 二进制码的转换

- 收获

- 1. robot的步骤的分解实现，  知道每一步的robot行为逻辑， 1.先发激活包， 2. 正常的协议交互， 3. 心跳包， 定期发送，超时前发送即可

- 2. 字节流截取，网络编程的基础

## 阅读erlang官方指引做的笔记以及知识点

- [erlang官方直营](https://www.erlang.org/doc/efficiency_guide/introduction.html)


- [minikube dictionary](../../kubernetes/minikube/dictionary.md)在kubernetes里也有个文档(不过跨文件和根目录的超链接似乎不生效，也可能是其本身的愈发问题，此处就先不管了，需要查看直接 去  kubernetes / minikube 查看)，新起一个dictionary 查字典去查询对应的新单词和术语

- [Erlang Dictionary](Dictionary.md)


### erlang 应用程序的几种运行方式（知识点1）

-	运行方式：

-	1.在erlang shell中编译运行

```erlang
-module(hello).
-export([start/0]).
 
start() ->
     io:format("Hello world~n").
```

```erlang
erl 
Erlang R14B03 (erts-5.8.4) [source] [smp:2:2] [rq:2] [async-threads:0] [hipe] [kernel-poll:false]
Eshell V5.8.4  (abort with ^G) 
1> c(hello). 
{ok,hello} 
2> hello: 
module_info/0  module_info/1  start/0
2> hello:start(). 
Hello world 
ok 
3> 
```
　
- 2 在命令行提示符下编译运行

```erlang
erlc hello.erl 
erl -noshell -s hello start -s init stop

```
快速脚本
```erlang
erl -eval 'io:format("Memory:~p~n",[erlang:memory(total)]).' -noshell -s init stop
```
3 当做escript脚本运行

```erlang
1 #!/usr/bin/escript
2 
3 main(_) ->
4     io:format("Hello World~n").


```

```bash
chmod 
+x hello 
./hello
```

- 以上就是erl运行的三种方式了

- 对于1，2都是比较好理解的例子 sample，直接在命令行下面进入 erl 的解释器，然后进行编译就好了， c(filename), 生成个对应的filename.beam ,然后运行 filename：函数名(). 就可以了

- 第2种整体也不算很难

- 第3种直接在作为可执行脚本直接调用，跳过编译步骤和前两种方法差别还是比较大的，进行尝试的时候发现也是经常不得要领，最后发现在windows端的话在命令行里（windows端就是  escript.exe filename.escript argus）使用这个命令就可以达成直接当成escript来运行的目的。

	- 详见例子中的 factorial.erl 及里面的注解。

- 而第3中方式在内网linux中也是一样，作为escript 直接 ./test.escript 在linux中一样有效，可以参看/lidai/test_Code目录看test.escript例子，在内网linux中运行生效。

- 但是回过来看，最常用的还是应该是第一种编译成beam形式的直接调用。


- 到此，erl运行环境问题得到解决。2023-03-06 15:10:28 by DailyR 

	

### 新的知识点


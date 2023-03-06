## 阅读erlang官方指引做的笔记以及知识点

- [erlang官方直营](https://www.erlang.org/doc/efficiency_guide/introduction.html)


- [minikube dictionary](../../kubernetes/minikube/dictionary.md)在kubernetes里也有个文档(不过跨文件和根目录的超链接似乎不生效，也可能是其本身的愈发问题，此处就先不管了，需要查看直接 去  kubernetes / minikube 查看)，新起一个dictionary 查字典去查询对应的新单词和术语

- [Erlang Dictionary](Dictionary.md)


- erlang 应用程序的几种运行方式


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
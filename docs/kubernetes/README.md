# DailysCodeDocs for Go & kubernetes

'''
··· coding  by myself
'''

### Go和kubernetes的一些学习经验和笔记

- 由于kubernetes涉及的概念较多，而且并不是具体到语言

- 大部分是是使用shell的命令行形式进行操控的，所以单独分类一个文件夹目录路径似乎并不合适

- 想着还是新建一个kubernetest【哭波奶踢丝】的路径，然后以md的形式，

- 进行学习笔记的记录会好些


- 选用里md，markdown格式来进行记录和书写

- md格式的相互引用

- [minikube](minikube/minikube.md)


### kubernetes的一些学习经验和笔记，库博乃提斯

- [k8s](https://kubernetes.io/docs/home/)

- [k8s overview 概述](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/)  Kubernetes 是一个可移植、可扩展的开源平台，用于管理容器化的工作负载和服务，可促进声明式配置和自动化。 Kubernetes 拥有一个庞大且快速增长的生态，其服务、支持和工具的使用范围相当广泛.

- [k8s进化论-时间回溯](minikube/Going_back_in_time.md)
- ![](imges/container_evolution.svg)
<!-- 
注释测试 -->

- [英语单词](minikube/dictionary.md)


### kubernetes的环境部署

- [kubectl]Kubernetes 命令行工具，kubectl，使得你可以对 Kubernetes 集群运行命令。 你可以使用 kubectl 来部署应用、监测和管理集群资源以及查看日志。

- [在 Windows 上安装 kubectl](https://kubernetes.io/zh-cn/docs/tasks/tools/install-kubectl-windows/)

- [choco](choco.md)

- 使用choco来进行安装命令行工具， 
	- choco install kubernetes-cli

	- 测试一下，确保安装的是最新版本：
	- kubectl version --client
	- 导航到你的 home 目录：
	- 当你用 cmd.exe 时，则运行： cd %USERPROFILE% ，其实一般都是在默认路径
	- cd ~
	- 创建目录 .kube：
	- mkdir .kube
	- 切换到新创建的目录 .kube
	- cd .kube
	- 配置 kubectl，以接入远程的 Kubernetes 集群：
	- New-Item config -type file

		- WARNING: This version information is deprecated and will be replaced with the output from kubectl version --short.  Use --output=yaml|json to get the full version.
		- Client Version: version.Info{Major:"1", Minor:"24", GitVersion:"v1.24.1", GitCommit:"3ddd0f45aa91e2f30c70734b175631bec5b5825a", GitTreeState:"clean", BuildDate:"2022-05-24T12:26:19Z", GoVersion:"go1.18.2", Compiler:"gc", Platform:"windows/amd64"}
		- Kustomize Version: v4.5.4

	- [cmd shell test](shell_cmd.md)

- [minikube](https://minikube.sigs.k8s.io/docs/start/)

	- minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.
	- 与 kind 类似，minikube 是一个工具， 能让你在本地运行 Kubernetes。 minikube 在你本地的个人计算机（包括 Windows、macOS 和 Linux PC）运行一个单节点的 Kubernetes 集群，以便你来尝试 Kubernetes 或者开展每天的开发工作。

	- 如果你关注如何安装此工具，可以按官方的 Get Started!指南操作。
- [minikube_local](/minikube/minikube.md)

	- choco install minikube
	- minikube start
	- minikube kubectl -- get po -A
	- alias kubectl="minikube kubectl --"
	- minikube dashboard


	- [If minikube fails to start, see the  drivers page一般没装docker环境那些都要在这里去安装的](https://minikube.sigs.k8s.io/docs/drivers/)

	- [docker install](https://minikube.sigs.k8s.io/docs/drivers/docker/)

	- Windows
		- Hyper-V - VM (preferred)
		- Docker - VM + Container (preferred)

	- [docker Hub](https://hub.docker.com/)
	- [docker windows install](https://docs.docker.com/desktop/windows/install/)
	- [docker windows example](docker.md)
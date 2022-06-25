

## [minikube](https://minikube.sigs.k8s.io/docs/start/)


- minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.

- All you need is Docker (or similarly compatible) container or a Virtual Machine environment, and Kubernetes is a single command away: minikube start

- 1. Installation

- 2. Start your cluster
      From a terminal with administrator access (but not logged in as root), run:

      minikube start
      If minikube fails to start, see the drivers page for help setting up a compatible container or virtual-machine manager.



- 3. Interact with your cluster
      If you already have kubectl installed, you can now use it to access your shiny new cluster:

      kubectl get po -A
      Alternatively, minikube can download the appropriate version of kubectl and you should be able to use it like this:

      minikube kubectl -- get po -A
      You can also make your life easier by adding the following to your shell config:

      alias kubectl="minikube kubectl --"
      Initially, some services such as the storage-provisioner, may not yet be in a Running state. This is a normal condition during cluster bring-up, and will resolve itself momentarily. For additional insight into your cluster state, minikube bundles the Kubernetes Dashboard, allowing you to get easily acclimated to your new environment:

      minikube dashboard

- 4. 4Deploy applications
      Create a sample deployment and expose it on port 8080:

      kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4
      kubectl expose deployment hello-minikube --type=NodePort --port=8080
      It may take a moment, but your deployment will soon show up when you run:

      kubectl get services hello-minikube
      The easiest way to access this service is to let minikube launch a web browser for you:

      minikube service hello-minikube
      Alternatively, use kubectl to forward the port:

      kubectl port-forward service/hello-minikube 7080:8080
      Tada! Your application is now available at http://localhost:7080/.

      You should be able to see the request metadata from nginx such as the CLIENT VALUES, SERVER VALUES, HEADERS RECEIVED and the BODY in the application output. Try changing the path of the request and observe the changes in the CLIENT VALUES. Similarly, you can do a POST request to the same and observe the body show up in BODY section of the output.

      LoadBalancer deployments



- C:\Users\Administrator>minikube service hello-minikube

|-----------|----------------|-------------|---------------------------|
| NAMESPACE |      NAME      | TARGET PORT |            URL            |
|-----------|----------------|-------------|---------------------------|
| default   | hello-minikube |        8080 | http://192.168.49.2:31102 |
|-----------|----------------|-------------|---------------------------|
* Starting tunnel for service hello-minikube.
|-----------|----------------|-------------|------------------------|
| NAMESPACE |      NAME      | TARGET PORT |          URL           |
|-----------|----------------|-------------|------------------------|
| default   | hello-minikube |             | http://127.0.0.1:63124 |
|-----------|----------------|-------------|------------------------|
* 正通过默认浏览器打开服务 default/hello-minikube...
! Because you are using a Docker driver on windows, the terminal needs to be open to run it.



- C:\Users\Administrator>minikube kubectl -- get po -A
NAMESPACE              NAME                                         READY   STATUS             RESTARTS        AGE
default                hello-minikube-5c5f5cddb9-ct7lc              1/1     Running            1 (6m42s ago)   32m
kube-system            coredns-6d4b75cb6d-f8dn9                     1/1     Running            4 (6m42s ago)   54m
kube-system            etcd-minikube                                1/1     Running            5 (6m42s ago)   54m
kube-system            kube-apiserver-minikube                      1/1     Running            5 (6m42s ago)   54m
kube-system            kube-controller-manager-minikube             1/1     Running            5 (6m42s ago)   54m
kube-system            kube-proxy-gshp4                             1/1     Running            6 (6m42s ago)   54m
kube-system            kube-scheduler-minikube                      1/1     Running            6 (6m42s ago)   54m
kube-system            storage-provisioner                          1/1     Running            4 (6m42s ago)   54m
kubernetes-dashboard   dashboard-metrics-scraper-78dbd9dbf5-sbpb2   1/1     Running            2 (6m42s ago)   43m
kubernetes-dashboard   kubernetes-dashboard-5fd5574d9f-fls2d        0/1     ImagePullBackOff   0               43m


- minikube service hello-minikube  上面可以看到自动打开浏览器
链接如下，然后就可以看到对应的参数，就是初始化有点久，耐心等待即可

http://127.0.0.1:63124/

CLIENT VALUES:
client_address=172.17.0.1
command=GET
real path=/
query=nil
request_version=1.1
request_uri=http://127.0.0.1:8080/

SERVER VALUES:
server_version=nginx: 1.10.0 - lua: 10001

HEADERS RECEIVED:
accept=text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
accept-encoding=gzip, deflate, br
accept-language=zh-CN,zh;q=0.9
connection=keep-alive
host=127.0.0.1:63124
sec-ch-ua=" Not A;Brand";v="99", "Chromium";v="102", "Google Chrome";v="102"
sec-ch-ua-mobile=?0
sec-ch-ua-platform="Windows"
sec-fetch-dest=document
sec-fetch-mode=navigate
sec-fetch-site=none
sec-fetch-user=?1
upgrade-insecure-requests=1
user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.0.0 Safari/537.36
BODY:
-no body in request-



- C:\Users\Administrator>kubectl port-forward service/hello-minikube 7080:8080
Forwarding from 127.0.0.1:7080 -> 8080
Forwarding from [::1]:7080 -> 8080
Handling connection for 7080
Handling connection for 7080


直接运行转发端口也可以结果跟上面一样


- C:\Users\Administrator>minikube dashboard
* 正在开启 dashboard ...
  - Using image registry.cn-hangzhou.aliyuncs.com/google_containers/dashboard:v2.6.0
  - Using image registry.cn-hangzhou.aliyuncs.com/google_containers/metrics-scraper:v1.0.8
* 正在验证 dashboard 运行情况 ...
* Launching proxy ...
* 正在验证 proxy 运行状况 ...
* Opening http://127.0.0.1:52939/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/ in your default browser...


- ![](../imges/MinkubeDashboard1.png)
- ![](../imges/MinkubeDashboard2.png)
- ![](../imges/Minkube-pCluseter2.png)
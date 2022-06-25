

C:\Users\Administrator\.kube>kubectl cluster-info


To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
Unable to connect to the server: dial tcp [::1]:8080: connectex: No connection could be made because the target machine actively refused it.



C:\Users\Administrator>minikube start

* Microsoft Windows 10 Enterprise Ltsc 2019 10.0.17763 Build 17763 上的 minikube v1.26.0
* Unable to pick a default driver. Here is what was considered, in preference order:
* Alternatively you could install one of these drivers:
  - docker: Not installed: exec: "docker": executable file not found in %PATH%·
  - hyperv: Not installed: C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -NoProfile -NonInteractive @(Get-CimInstance Win32_ComputerSystem).HypervisorPresent returned "False\r\n"
  - vmware: Not installed: exec: "docker-machine-driver-vmware": executable file not found in %PATH%
  - virtualbox: Not installed: unable to find VBoxManage in $PATH
  - podman: Not installed: exec: "podman": executable file not found in %PATH%
  - qemu2: Not installed: exec: "qemu-system-x86_64": executable file not found in %PATH%

X Exiting due to DRV_NOT_DETECTED: No possible driver was detected. Try specifying --driver, or see https://minikube.sigs.k8s.io/docs/start/


安装完成docker之后，再运行minikube start：

- [minikube](https://minikube.sigs.k8s.io/docs/start/)
C:\Users\Administrator>minikube start
* Microsoft Windows 10 Enterprise Ltsc 2019 10.0.17763 Build 17763 上的 minikube v1.26.0
* 自动选择 docker 驱动。其他选项：hyperv, ssh
* Using Docker Desktop driver with root privileges
* Starting control plane node minikube in cluster minikube
* Pulling base image ...
* Downloading Kubernetes v1.24.1 preload ...
    > preloaded-images-k8s-v18-v1...: 205.25 MiB / 405.83 MiB  50.58% 237.55 Ki


C:\Users\Administrator>minikube start

* Microsoft Windows 10 Enterprise Ltsc 2019 10.0.17763 Build 17763 上的 minikube v1.26.0
* 自动选择 docker 驱动。其他选项：hyperv, ssh
* Using Docker Desktop driver with root privileges
* Starting control plane node minikube in cluster minikube
* Pulling base image ...
* Downloading Kubernetes v1.24.1 preload ...
    > gcr.io/k8s-minikube/kicbase: 386.00 MiB / 386.00 MiB  100.00% 238.47 KiB
    > preloaded-images-k8s-v18-v1...: 405.83 MiB / 405.83 MiB  100.00% 245.59 K
    > gcr.io/k8s-minikube/kicbase: 0 B [______________________] ?% ? p/s 14m19s
* Creating docker container (CPUs=2, Memory=1952MB) ...
* 正在 Docker 20.10.17 中准备 Kubernetes v1.24.1…
  - Generating certificates and keys ...
  - Booting up control plane ...
  - Configuring RBAC rules ...
* Verifying Kubernetes components...
  - Using image gcr.io/k8s-minikube/storage-provisioner:v5
* Enabled addons: storage-provisioner, default-storageclass
* Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default


C:\Users\Administrator>minikube start

* Microsoft Windows 10 Enterprise Ltsc 2019 10.0.17763 Build 17763 上的 minikube v1.26.0
* 根据现有的配置文件使用 docker 驱动程序
* Starting control plane node minikube in cluster minikube
* Pulling base image ...
* Updating the running docker "minikube" container ...
* 正在 Docker 20.10.17 中准备 Kubernetes v1.24.1…
* Verifying Kubernetes components...
  - Using image gcr.io/k8s-minikube/storage-provisioner:v5
* Enabled addons: storage-provisioner, default-storageclass
* Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default




C:\Users\Administrator>kubectl get po -A

NAMESPACE     NAME                               READY   STATUS    RESTARTS      AGE
kube-system   coredns-6d4b75cb6d-f8dn9           1/1     Running   1 (34s ago)   10m
kube-system   etcd-minikube                      1/1     Running   2 (34s ago)   10m
kube-system   kube-apiserver-minikube            1/1     Running   2 (24s ago)   10m
kube-system   kube-controller-manager-minikube   1/1     Running   2 (34s ago)   10m
kube-system   kube-proxy-gshp4                   1/1     Running   2 (34s ago)   10m
kube-system   kube-scheduler-minikube            1/1     Running   2 (24s ago)   10m
kube-system   storage-provisioner                1/1     Running   1 (39s ago)   10m


C:\Users\Administrator>minikube dashboard

* 正在开启 dashboard ...
  - Using image kubernetesui/dashboard:v2.6.0
  - Using image kubernetesui/metrics-scraper:v1.0.8
* 正在验证 dashboard 运行情况 ...
* Launching proxy ...
* 正在验证 proxy 运行状况 ...

X Exiting due to SVC_URL_TIMEOUT: http://127.0.0.1:57977/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/ is not accessible: Temporary Error: unexpected response code: 503


C:\Users\Administrator>kubectl get po -A

NAMESPACE              NAME                                         READY   STATUS              RESTARTS      AGE
default                hello-minikube-5c5f5cddb9-ct7lc              1/1     Running             1 (52s ago)   26m
kube-system            coredns-6d4b75cb6d-f8dn9                     1/1     Running             4 (52s ago)   48m
kube-system            etcd-minikube                                1/1     Running             5 (52s ago)   48m
kube-system            kube-apiserver-minikube                      1/1     Running             5 (52s ago)   48m
kube-system            kube-controller-manager-minikube             1/1     Running             5 (52s ago)   48m
kube-system            kube-proxy-gshp4                             1/1     Running             6 (52s ago)   48m
kube-system            kube-scheduler-minikube                      1/1     Running             6 (52s ago)   48m
kube-system            storage-provisioner                          1/1     Running             4 (52s ago)   48m
kubernetes-dashboard   dashboard-metrics-scraper-78dbd9dbf5-sbpb2   1/1     Running             2 (52s ago)   37m
kubernetes-dashboard   kubernetes-dashboard-5fd5574d9f-fls2d        0/1     ContainerCreating   0             37m

C:\Users\Administrator>minikube kubectl -- get po -A

NAMESPACE              NAME                                         READY   STATUS              RESTARTS      AGE
default                hello-minikube-5c5f5cddb9-ct7lc              1/1     Running             1 (87s ago)   27m
kube-system            coredns-6d4b75cb6d-f8dn9                     1/1     Running             4 (87s ago)   49m
kube-system            etcd-minikube                                1/1     Running             5 (87s ago)   49m
kube-system            kube-apiserver-minikube                      1/1     Running             5 (87s ago)   49m
kube-system            kube-controller-manager-minikube             1/1     Running             5 (87s ago)   49m
kube-system            kube-proxy-gshp4                             1/1     Running             6 (87s ago)   49m
kube-system            kube-scheduler-minikube                      1/1     Running             6 (87s ago)   49m
kube-system            storage-provisioner                          1/1     Running             4 (87s ago)   49m
kubernetes-dashboard   dashboard-metrics-scraper-78dbd9dbf5-sbpb2   1/1     Running             2 (87s ago)   37m
kubernetes-dashboard   kubernetes-dashboard-5fd5574d9f-fls2d        0/1     ContainerCreating   0             37m

C:\Users\Administrator>minikube dashboard

* 正在验证 dashboard 运行情况 ...
* Launching proxy ...
* 正在验证 proxy 运行状况 ...




Clean up
Now you can clean up the resources you created in your cluster:

kubectl delete service hello-node
kubectl delete deployment hello-node
Optionally, stop the Minikube virtual machine (VM):

minikube stop
Optionally, delete the Minikube VM:

minikube delete




C:\Users\Administrator>minikube start --image-mirror-country=cn

* Microsoft Windows 10 Enterprise Ltsc 2019 10.0.17763 Build 17763 上的 minikube v1.26.0
* 自动选择 docker 驱动。其他选项：hyperv, ssh
* 正在使用镜像存储库 registry.cn-hangzhou.aliyuncs.com/google_containers
* Using Docker Desktop driver with root privileges
* Starting control plane node minikube in cluster minikube
* Pulling base image ...
    > registry.cn-hangzhou.aliyun...: 0 B [_____________________] ?% ? p/s 3m6s
* Creating docker container (CPUs=2, Memory=1952MB) ...
* 正在 Docker 20.10.17 中准备 Kubernetes v1.24.1…
  - Generating certificates and keys ...
  - Booting up control plane ...
  - Configuring RBAC rules ...
* Verifying Kubernetes components...
  - Using image registry.cn-hangzhou.aliyuncs.com/google_containers/storage-provisioner:v5
* Enabled addons: storage-provisioner, default-storageclass
* Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default

- 使用阿里云的镜像，速度会快很多

- 关注Ready状态
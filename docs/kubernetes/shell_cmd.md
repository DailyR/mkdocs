

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
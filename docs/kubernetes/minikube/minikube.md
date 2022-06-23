

- minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.

- Interact with your cluster
If you already have kubectl installed, you can now use it to access your shiny new cluster:

kubectl get po -A
Alternatively, minikube can download the appropriate version of kubectl and you should be able to use it like this:

minikube kubectl -- get po -A
You can also make your life easier by adding the following to your shell config:

alias kubectl="minikube kubectl --"
Initially, some services such as the storage-provisioner, may not yet be in a Running state. This is a normal condition during cluster bring-up, and will resolve itself momentarily. For additional insight into your cluster state, minikube bundles the Kubernetes Dashboard, allowing you to get easily acclimated to your new environment:

minikube dashboard
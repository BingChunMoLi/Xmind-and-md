```shell
kubeadm reset
kubeadm init
```

安装成功note：
```note
Your Kubernetes control-plane has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join 192.168.10.133:6443 --token qztpum.15gik4j4er2tpmyc \
    --discovery-token-ca-cert-hash sha256:487787769519a5ca46330500ec24375b5b1a72d4680c3370dd99967089e02c62
```
Before start, we validate the k8s is started.

`launch.sh`{{execute}}

Join the worker node to master. But before that we need to locate the master IP.

`ifconfig ens3`{{execute HOST1}}

`kubeadm join xxx.xxx.xxx.xxx:6443 --token=96771a.f608976060d16396 --discovery-token-unsafe-skip-ca-verification`{{copy}}

Make sure all k8s node is ready.

`kubectl get node`{{execute HOST1}}


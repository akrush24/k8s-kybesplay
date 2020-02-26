Installation
```
# git clone https://github.com/kubernetes-sigs/kubespray.git
# cd ./kubespray && git checkout v2.12.1 && cd ..
# sudo pip install -r kubespray/requirements.txt
# cp -rfp ./kubespray/inventory/sample mycluster
# vi ./kubespray/inventory/sample/group_vars/k8s-cluster/k8s-cluster.yml
-kube_network_plugin: calico
+kube_network_plugin: flannel
# ansible-playbook -i ./mycluster/inventory.ini kubespray/cluster.yml
```

```
[root@m01k8s ~]# kubectl  get nodes
NAME               STATUS   ROLES    AGE   VERSION
m01k8s.srv.local   Ready    master   12m   v1.16.7
m02k8s.srv.local   Ready    master   11m   v1.16.7
m03k8s.srv.local   Ready    master   11m   v1.16.7
n01k8s.srv.local   Ready    <none>   10m   v1.16.7
n02k8s.srv.local   Ready    <none>   10m   v1.16.7
n03k8s.srv.local   Ready    <none>   10m   v1.16.7

[root@m01k8s ~]# kubectl label nodes n01k8s.srv.local node-role.kubernetes.io/node=
node/n01k8s.srv.local labeled
[root@m01k8s ~]# kubectl label nodes n02k8s.srv.local node-role.kubernetes.io/node=
node/n02k8s.srv.local labeled
[root@m01k8s ~]# kubectl label nodes n03k8s.srv.local node-role.kubernetes.io/node=
node/n03k8s.srv.local labeled

[root@m01k8s ~]# kubectl  get nodes
NAME               STATUS   ROLES    AGE   VERSION
m01k8s.srv.local   Ready    master   13m   v1.16.7
m02k8s.srv.local   Ready    master   12m   v1.16.7
m03k8s.srv.local   Ready    master   12m   v1.16.7
n01k8s.srv.local   Ready    node     11m   v1.16.7
n02k8s.srv.local   Ready    node     11m   v1.16.7
n03k8s.srv.local   Ready    node     10m   v1.16.7
```

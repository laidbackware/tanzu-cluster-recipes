# TKGS setup
```
kubectl-vsphere login --server=172.20.2.1 --insecure-skip-tls-verify --vsphere-username administrator@vsphere.local

kubectx 172.20.2.1

kubectl api-resources |grep vmware

ka tkg-cluster1.yml

k get tanzukubernetesclusters -n ns1
```
## Guest cluster login
```
kubectl vsphere login --server=172.20.2.1 --vsphere-username administrator@vsphere.local --tanzu-kubernetes-cluster-name tkgs-demo-1 --tanzu-kubernetes-cluster-namespace ns1 --insecure-skip-tls-verify
kubectl vsphere login --server=172.20.2.1 --vsphere-username administrator@vsphere.local --tanzu-kubernetes-cluster-name tkgs-demo-2 --tanzu-kubernetes-cluster-namespace ns2 --insecure-skip-tls-verify

kubectx tkgs-demo-1
```
## Setup PSPs
```
kubectl create clusterrolebinding psp:authenticated  --clusterrole=psp:vmware-system-privileged --group=system:authenticated
```



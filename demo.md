# demo commands
kubectl-vsphere login --server=172.20.2.1 --insecure-skip-tls-verify --vsphere-username administrator@vsphere.local

kubectx 172.20.2.1

ka tkg-cluster1.yml
ka tkg-cluster2.yml

k get tanzukubernetesclusters -n ns1

kubectl api-resources |grep vmware

kubectl vsphere login --server=172.20.2.1 --vsphere-username administrator@vsphere.local --tanzu-kubernetes-cluster-name tkgs-demo-1 --tanzu-kubernetes-cluster-namespace ns1 --insecure-skip-tls-verify
kubectl vsphere login --server=172.20.2.1 --vsphere-username administrator@vsphere.local --tanzu-kubernetes-cluster-name tkgs-demo-2 --tanzu-kubernetes-cluster-namespace ns2 --insecure-skip-tls-verify

kubectx tkgs-demo-1

# Setup PSPs
kubectl create clusterrolebinding psp:authenticated  --clusterrole=psp:vmware-system-privileged --group=system:authenticated

## tidy up

k config delete-context 172.20.2.1
k config delete-context ns1
k config delete-context tkgs-demo

# Network Policy

k create ns network-policy-demo

kubectl run --rm -i --tty curl-pod --image=laidbackware/asdf-tools-test:v1 -n network-policy-demo -- /bin/bash

curl -v http://vcsa.home.local
curl -v https://vcsa.home.local


# Storage

k get tanzukubernetesclusters --all-namespaces

## Set storage class as default
kubectx tkgs-demo-1

k describe storageclass tkgs-storage-policy


## Deploy postfacto
/home/matt/workspace/projects/archive/postfacto/deployment/deploy-tkg.sh postfacto

## Deploy Minio
ka velero-minio-deployment.yml -n velero


kubectx tkgs-demo-2



## Tekton

kubectl api-resources

kubectl apply -f release.yml

kubectl api-resources

k get tasks
k get taskruns

kubectl apply -f task-hello.yml

k get tasks

tkn task start hello

k get taskruns

tkn taskrun logs --last -f

kubectl delete -f release.yml

## Tanzu

kubectl-vsphere login --server=172.20.2.1 --insecure-skip-tls-verify --vsphere-username administrator@vsphere.local

kubectx 172.20.2.1

kubectl api-resources |grep vmware

k get tanzukubernetesclusters
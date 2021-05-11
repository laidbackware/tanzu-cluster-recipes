# Tekton Demo

```
kubectl api-resources

kubectl apply -f tekton/release.yml

kubectl api-resources

k get tasks
k get taskruns

kubectl apply -f tekton/task-hello.yml

k get tasks

tkn task start hello

k get taskruns

tkn taskrun logs --last -f

kubectl delete -f tekton/release.yml
```
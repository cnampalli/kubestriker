# kubestriker
This repository contains code/helm charts for deploying kubestriker on a k8s cluster/namespace

## Create k8s namespace
Run the commands below to create the kubernetes namespace for kubestriker application

```
export K8S_NAMESPACE="kubestriker"
kubectl create namespace ${K8S_NAMESPACE}
```
## dynamodb deployment
Run the below commands

```
kubectl create -f kubestriker-db-service.yaml --namespace=${K8S_NAMESPACE}
kubectl create -f kubestriker-db.yaml --namespace=${K8S_NAMESPACE}
```

## neo4j backend service setup
```
kubectl create -f neo4j-common-config.yaml --namespace=${K8S_NAMESPACE}
kubectl apply -f neo4j-core-config.yaml --namespace=${K8S_NAMESPACE}
kubectl create -f neo4j-discovery-lb.yaml --namespace=${K8S_NAMESPACE}
```
## main kubestriker python container setup
```
kubectl create -f kubestriker-python-svc.yaml --namespace=${K8S_NAMESPACE}
kubectl create -f kubestriker.yaml --namespace=${K8S_NAMESPACE}
```
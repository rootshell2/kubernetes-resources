# Kubernetes Deployments

## Deploy a stateful application

How to deploy a application using StatefulSets

**File** | **Content**
------------ | -------------
**azure-PersistentVolumeClaim-secret.yml** | Creates a Kubernetes secret which holds both the account name and key for Microsoft Azure storage account. (sensitive data was removed)
**azure-PersistentVolumeClaim.yml** | Mount the Azure File Storage using a Persistent Volume and a Persistent Volume Claim.
**azure-PersistentVolumeClaim-claim.yml** | Persistent Volume Claim.
**azure-PersistentVolumeClaim-pod.yml** | Create a stateful set of pods with _persistent volume_ claims.
**basic-ingress.yaml** | _Ingress_ resources map
**service.yaml** | _Service_ exposing Nginx test server
**helloworld.sh** |Deploys and exposes a extra Nginx test server on TCP/8080


**Create the secret**
```console
$ kubectl -f azure-PersistentVolumeClaim-secret.yml
```
**Persistent Volume using  _azureFile_**
```console
$ kubectl -f azure-PersistentVolumeClaim.yml
```
**Persistent Volume Claim matching the Volume**
```console
$ kubectl -f azure-PersistentVolumeClaim-claim.yml
```

**Create a stateful set of pods with persistent volume claims**
```console
$ kubectl -f azure-PersistentVolumeClaim-pod.yml
```


## NGINX Ingress Controller.
Kubernetes ingress is a collection of routing rules that govern how external users access services running in a Kubernetes cluster.

**File** | **Content**
------------ | -------------
**mandatory.yaml** | Resources for complete Nginx Ingress Controller deployment.
**service-nodeport.yaml** | Creating a Kubernetes service of type NodePort
**nginx-ingress-version.sh** | To detect which version of the ingress controller is running, exec into the pod and run `nginx-ingress-controller version` command.


**Creates _Kubernetes Ingress_ resources for a generic deployment**
```console
$ kubectl -f mandatory.yaml
```
**Creates a service of type _NodePort_ and connect itself to _Ingress_**
```console
$ kubectl -f service-nodeport.yaml
```
**Shows the version of Nginx Ingress running on the _Pods_**
```console
$ kubectl -f nginx-ingress-version.sh
```

[http://hellotravix.kubetest.cf:30936/](http://hellotravix.kubetest.cf:30936/)
[http://helloworld.kubetest.cf:30936/](http://helloworld.kubetest.cf:30936/)  
[http://40.87.6.237:30936](http://40.87.6.237:30936)/  (default backend 404)


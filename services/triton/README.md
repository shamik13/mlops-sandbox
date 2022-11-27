# Triton
This will deploy NVIDIA Triton inference server (https://catalog.ngc.nvidia.com/orgs/nvidia/containers/tritonserver) along with Minio object storage. 
## Deployment guide:
How to install?
 ```
      >>> cd service/triton
      >>> kubectl create ns triton
      >>> kubectl apply -f minio.yaml -n triton
      >>> kubectl apply -f triton.yaml -n triton
```

Ingress related settings:
1. Find the IP address of Minikube. 
```
  >>> minikube ip
```

2. Edit `/etc/hosts` to add the following entries along with <minikube-ip> found in the previous step:
```
<minikube-ip>   triton-server.mlops-sandbox.com triton-minio.mlops-sandbox.com triton-minio-console.mlops-sandbox.com
```


How to uninstall?
```     
      >>> ce service/triton
      >>> kubectl delete -f minio.yaml -n triton
      >>> kubectl delete -f triton.yaml -n triton
```
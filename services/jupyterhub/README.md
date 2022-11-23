# JupyterHub
This will deploy Jupyterhub environment where each user will have their own Notebook compute environment as well as personal and shared storage. 
## Deployment guide:
How to install?
 ```
      >>> cd service
      >>> docker pull jupyter/minimal-notebook:hub-3.0.0
      >>> docker pull jupyter/scipy-notebook:9e63909e0317
      >>> minikube image load jupyter/minimal-notebook:hub-3.0.0
      >>> minikube image load jupyter/scipy-notebook:9e63909e0317
      >>> helm install release-1 -n z2jh ./jupyterhub --create-namespace
```

Ingress related settings:
1. Find the IP address of Minikube. 
```
  >>> minikube ip
```

2. Edit `/etc/hosts` to add the following entries along with <minikube-ip> found in the previous step:
```
<minikube-ip>   mlops-sandbox.com
```

How to uninstall?
```     
      >>> helm uninstall release-1 -n z2jh
```
You may have to delete PVCs and PVs manually.

For more details about what each variable does in `Values.yaml`, please follow https://z2jh.jupyter.org/en/stable/
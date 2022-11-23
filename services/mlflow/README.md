# MLflow
This will deploy MLflow tracking server along with Minio object storage and Postgres relational database. The default settings of this MLflow deployment is also configured in Jupyterhub so that Jupyterhub users can use MLflow out of the box. 
## Deployment guide:
How to install?
 ```
      >>> cd service/mlflow
      >>> docker build -t mlflow:v1 .
      >>> minikube image load mlflow:v1
      >>> kubectl create ns mlflow
      >>> kubectl apply -f postgres.yaml -n mlflow
      >>> kubectl apply -f minio.yaml -n mlflow
      >>> kubectl apply -f mlflow.yaml -n mlflow
```

Ingress related settings:
1. Find the IP address of Minikube. 
```
  >>> minikube ip
```

2. Edit `/etc/hosts` to add the following entries along with <minikube-ip> found in the previous step:
```
<minikube-ip>   mlflow.mlops-sandbox.com minio.mlops-sandbox.com minio-console.mlops-sandbox.com
```


How to uninstall?
```     
      >>> ce service/mlflow
      >>> kubectl delete -f postgres.yaml -n mlflow
      >>> kubectl delete -f minio.yaml -n mlflow
      >>> kubectl delete -f mlflow.yaml -n mlflow
```
You may have to delete PVCs and PVs manually.
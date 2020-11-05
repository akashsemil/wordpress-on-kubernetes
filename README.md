# wordpress-on-kubernetes

Deploy Wordpress on Kubernetes using Deployment, Configmap, Secret, Service.

## Working
Deployment Object consist of template for three containers nginx, WordPress with php-fpm and mariadb.With ConfigMaps we are able to store nginx configuration file, With Secrets we are able to store sensitive information like database credentials, With Service client are able to connect and at last using host volume to store persistent data.

## Tested on minikube

Make sure to enable following addons on minikube

```bash
$ minikube start
$ minikube addons add ingress
$ minikube addons add metrics-server
```
You can check whether the above addons are enabled or not.
```bash
$ minikube addons list
```

## Usage
### Deploy Application

```bash
$ kubectl apply -f https://raw.githubusercontent.com/akashsemil/wordpress-on-kubernetes/main/wordpress-example.yaml
```
### Access the wordpress
Use the EXTERNAL-IP assigned to the service

```bash
$ kubectl get svc -l app=wordpress-example
```
If EXTERNAL-IP is <pending> make sure to run following and check again
```bash
$ minikube tunnel
```
### Delete Application
```bash
$ kubectl delete -f https://raw.githubusercontent.com/akashsemil/wordpress-on-kubernetes/main/wordpress-example.yaml
```
## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

### Steps of running

1. in command line create folders on worker node (eg.: ssh node001) for volumes:

```bash
mkdir /drupal-data
mkdir /drupal-mysql-data
```
2. create persistent volumes on master node

```bash
kubectl create -f persistent-volumes.yaml
```

3. create persistent volume claims on master node

```bash
kubectl create -f persistent-volume-claims.yaml
```

4. create secrets

```bash
kubectl create secret generic drupal-mysql-secret --from-literal=MYSQL_ROOT_PASSWORD=root_password --from-literal=MYSQL_DATABASE=drupal-database --from-literal=MYSQL_USER=root
```

5. create mysql deployment and service

```bash
kubectl create -f mysql-deployment.yaml
kubectl create -f mysql-service.yaml
```

6. create drupal deployment and service

```bash
kubectl create -f drupal-deployment.yaml
kubectl create -f drupal-service.yaml
```

7. Check that Drupal server works on port 30095 
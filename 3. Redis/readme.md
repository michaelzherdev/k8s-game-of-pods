### Steps of running

1. create persistent volumes

```bash
kubectl create -f pv.yaml
```

2. in command line create folders on worker node (eg.: ssh node001) for volumes:

```bash
mkdir /redis01
mkdir /redis02
mkdir /redis03
mkdir /redis04
mkdir /redis05
mkdir /redis06
```
3. create redis Stateful set

```bash
kubectl create -f set.yaml
```

4. create service

```bash
kubectl create -f service.yaml
```

5. Configure the Cluster. Once the StatefulSet has been deployed with 6 'Running' pods, run the below commands and type 'yes' when prompted.
```bash
kubectl exec -it redis-cluster-0 -- redis-cli --cluster create --cluster-replicas 1 $(kubectl get pods -l app=redis-cluster -o jsonpath='{range.items[*]}{.status.podIP}:6379 ')
```
### Steps of running

1. create persistent volume and persistent volume claim

```bash
kubectl create -f pv.yaml
```

2. create pod of file server

```bash
kubectl create -f pod.yaml
```

3. create service

```bash
kubectl create -f service.yaml
```

4. Check that File server works on port 31200 
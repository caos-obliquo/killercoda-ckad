## Solution

```bash
kubectl create namespace neptune 2>/dev/null || true

kubectl -n neptune create deploy neptune-10ab --replicas=3 --image=httpd:2.4-alpine --dry-run=client -oyaml > 21.yaml
```

Edit `21.yaml`:
```yaml
spec:
  template:
    spec:
      serviceAccountName: neptune-sa-v2
      containers:
      - image: httpd:2.4-alpine
        name: neptune-pod-10ab
        resources:
          limits:
            memory: 50Mi
          requests:
            memory: 20Mi
```

```bash
kubectl create -f 21.yaml
kubectl -n neptune get pod | grep neptune-10ab
```

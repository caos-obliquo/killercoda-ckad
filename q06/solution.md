## Solution

```bash
kubectl run pod6 --image=busybox:1.31.0 --dry-run=client -oyaml --command -- sh -c "touch /tmp/ready && sleep 1d" > 6.yaml
```

Edit `6.yaml` to add the readinessProbe:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod6
spec:
  containers:
  - command:
    - sh
    - -c
    - touch /tmp/ready && sleep 1d
    image: busybox:1.31.0
    name: pod6
    readinessProbe:
      exec:
        command:
        - sh
        - -c
        - cat /tmp/ready
      initialDelaySeconds: 5
      periodSeconds: 10
```

```bash
kubectl -f 6.yaml create
kubectl get pod pod6 --watch
```

## Solution

```bash
kubectl create namespace mercury 2>/dev/null || true
cp /opt/course/16/cleaner.yaml /opt/course/16/cleaner-new.yaml
```

Edit `/opt/course/16/cleaner-new.yaml` — add under `initContainers:` (sidecar pattern):
```yaml
- name: logger-con
  image: busybox:1.31.0
  restartPolicy: Always
  command: ["sh", "-c", "tail -f /var/log/cleaner/cleaner.log"]
  volumeMounts:
  - name: logs
    mountPath: /var/log/cleaner
```

```bash
kubectl -f /opt/course/16/cleaner-new.yaml apply
kubectl -n mercury get pod
kubectl -n mercury logs <pod-name> -c logger-con
```

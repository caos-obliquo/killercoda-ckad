## Solution

```bash
kubectl create namespace mars 2>/dev/null || true
cp /opt/course/17/test-init-container.yaml ~/17_test-init-container.yaml
```

Edit `~/17_test-init-container.yaml` — add `initContainers:` section:
```yaml
initContainers:
- name: init-con
  image: busybox:1.31.0
  command: ['sh', '-c', 'echo "check this out!" > /tmp/web-content/index.html']
  volumeMounts:
  - name: web-content
    mountPath: /tmp/web-content
```

```bash
kubectl -f ~/17_test-init-container.yaml create

# Get pod IP
kubectl -n mars get pod -o wide

# Test
kubectl run tmp --restart=Never --rm -i --image=nginx:alpine -- curl <POD_IP>
# Expected output: check this out!
```

## Solution

```bash
kubectl create namespace moon 2>/dev/null || true

# Create configmap with the correct key name
kubectl -n moon create configmap configmap-web-moon-html   --from-file=index.html=/opt/course/15/web-moon.html

# Wait for pods to restart
kubectl -n moon get pod -w
```

Test:
```bash
# Get a pod IP
kubectl -n moon get pod -o wide

# Curl from a temporary pod
kubectl run tmp --restart=Never --rm -i --image=nginx:alpine -- curl <POD_IP>
```

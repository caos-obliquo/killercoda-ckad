## Solution

```bash
cp /opt/course/9/holy-api-pod.yaml /opt/course/9/holy-api-deployment.yaml
```

Edit the file to wrap the Pod spec in a Deployment:
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: holy-api
  namespace: pluto
spec:
  replicas: 3
  selector:
    matchLabels:
      id: holy-api
  template:
    # --- paste original pod metadata and spec below ---
    metadata:
      labels:
        id: holy-api
    spec:
      containers:
      - name: holy-api-container
        image: nginx:1.17.3-alpine
        securityContext:
          allowPrivilegeEscalation: false
          privileged: false
        # ... rest of original spec
```

```bash
kubectl -f /opt/course/9/holy-api-deployment.yaml create
kubectl -n pluto delete pod holy-api --force --grace-period=0
kubectl -n pluto get pod,deployment | grep holy
```

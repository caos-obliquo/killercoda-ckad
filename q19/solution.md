## Solution

```bash
kubectl create namespace jupiter 2>/dev/null || true

# Check current state
kubectl -n jupiter get all

# Edit the service
kubectl -n jupiter edit service jupiter-crew-svc
```

Changes to make:
```yaml
spec:
  type: NodePort    # change from ClusterIP
  ports:
  - port: 8080
    targetPort: 80
    nodePort: 30100  # add this
```

```bash
# Verify
kubectl -n jupiter get svc

# Get node internal IPs
kubectl get nodes -o wide

# Test from main terminal
curl <NODE_INTERNAL_IP>:30100
```

> The Service is reachable on ALL nodes regardless of where the Pod is running.

## Solution

```bash
kubectl create namespace mars 2>/dev/null || true

# Check service
kubectl -n mars describe service manager-api-svc
# Notice: Endpoints: <none>

# Check what labels the pods have
kubectl -n mars get pod --show-labels

# Edit the service
kubectl -n mars edit service manager-api-svc
```

**Fix:** The service selector was pointing to `id: manager-api-deployment` but the Pods have label `id: manager-api-pod`.

Change selector to:
```yaml
selector:
  id: manager-api-pod
```

```bash
# Verify
kubectl -n mars get endpointslice
kubectl -n mars run tmp --restart=Never --rm -i --image=nginx:alpine -- curl -m 5 manager-api-svc:4444
```

## Solution

```bash
kubectl -n neptune rollout history deploy api-new-c32
kubectl -n neptune get deploy,pod | grep api-new-c32

# Find the failing pod
kubectl -n neptune describe pod <failing-pod-name> | grep -i image
kubectl -n neptune describe pod <failing-pod-name> | grep -i error
```

**Error:** The image was misspelled as `ngnix:1-alpine` instead of `nginx:1-alpine`.

```bash
# Rollback to the previous working revision
kubectl -n neptune rollout undo deploy api-new-c32

# Verify
kubectl -n neptune get deploy api-new-c32
```

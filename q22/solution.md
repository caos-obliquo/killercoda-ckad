## Solution

```bash
kubectl create namespace sun 2>/dev/null || true

# Check current pods and labels
kubectl -n sun get pod --show-labels

# Add label to workers and runners
kubectl -n sun label pod -l "type in (worker,runner)" protected=true

# Verify
kubectl -n sun get pod --show-labels

# Add annotation to all protected pods
kubectl -n sun annotate pod -l protected=true protected="do not delete this pod"

# Verify annotation
kubectl -n sun get pod -l protected=true -o yaml | grep -A8 metadata:
```

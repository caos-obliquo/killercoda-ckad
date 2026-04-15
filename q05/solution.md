## Solution

```bash
kubectl create namespace neptune 2>/dev/null || true
mkdir -p /opt/course/5

# Find secrets with service account annotation
kubectl -n neptune get secrets -oyaml | grep "service-account.name" -A1

# Or describe all secrets and look for neptune-sa-v2
kubectl -n neptune get secrets
kubectl -n neptune describe secret <secret-name>
```

The token shown by `describe` is already decoded. Copy it:
```bash
kubectl -n neptune describe secret neptune-secret-1 | grep "^token:" | awk '{print $2}' > /opt/course/5/token
```

Or decode manually:
```bash
kubectl -n neptune get secret neptune-secret-1 -o jsonpath='{.data.token}' | base64 -d > /opt/course/5/token
```

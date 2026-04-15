## Solution

```bash
kubectl create namespace earth 2>/dev/null || true
```

Create `12_pv.yaml`:
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: earth-project-earthflower-pv
spec:
  capacity:
    storage: 2Gi
  accessModes:
  - ReadWriteOnce
  hostPath:
    path: "/Volumes/Data"
```

Create `12_pvc.yaml`:
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: earth-project-earthflower-pvc
  namespace: earth
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 2Gi
```

```bash
kubectl create -f 12_pv.yaml
kubectl create -f 12_pvc.yaml
kubectl -n earth get pv,pvc

# Create deployment with volume mount
kubectl -n earth create deploy project-earthflower --image=httpd:2.4.41-alpine --dry-run=client -oyaml > 12_dep.yaml
# Edit to add volume/volumeMount referencing earth-project-earthflower-pvc at /tmp/project-data
kubectl create -f 12_dep.yaml
```

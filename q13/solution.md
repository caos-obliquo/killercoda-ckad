## Solution

```bash
kubectl create namespace moon 2>/dev/null || true
mkdir -p /opt/course/13
```

`13_sc.yaml`:
```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: moon-retain
provisioner: moon-retainer
reclaimPolicy: Retain
```

`13_pvc.yaml`:
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: moon-pvc-126
  namespace: moon
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 3Gi
  storageClassName: moon-retain
```

```bash
kubectl create -f 13_sc.yaml
kubectl create -f 13_pvc.yaml
kubectl -n moon describe pvc moon-pvc-126
# Copy the event message into:
echo "Waiting for a volume to be created either by the external provisioner 'moon-retainer' or manually by the system administrator. If volume creation is delayed, please verify that the provisioner is running and correctly registered." > /opt/course/13/pvc-126-reason
```

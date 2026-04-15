## Solution

```bash
kubectl create namespace moon 2>/dev/null || true
kubectl -n moon create secret generic secret1 --from-literal user=test --from-literal pass=pwd
kubectl -n moon create -f /opt/course/14/secret2.yaml

cp /opt/course/14/secret-handler.yaml /opt/course/14/secret-handler-new.yaml
```

Edit `/opt/course/14/secret-handler-new.yaml` — add to `spec.volumes`:
```yaml
- name: secret2-volume
  secret:
    secretName: secret2
```

Add to `spec.containers[0].volumeMounts`:
```yaml
- name: secret2-volume
  mountPath: /tmp/secret2
```

Add to `spec.containers[0].env`:
```yaml
- name: SECRET1_USER
  valueFrom:
    secretKeyRef:
      name: secret1
      key: user
- name: SECRET1_PASS
  valueFrom:
    secretKeyRef:
      name: secret1
      key: pass
```

```bash
kubectl -f /opt/course/14/secret-handler-new.yaml replace --force --grace-period=0
kubectl -n moon exec secret-handler -- env | grep SECRET1
```

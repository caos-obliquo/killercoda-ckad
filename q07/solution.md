## Solution

```bash
# Find the pod
kubectl -n saturn get pod -o yaml | grep my-happy-shop -A10
# OR
kubectl -n saturn describe pod | grep -i my-happy-shop

# Export the pod yaml
kubectl -n saturn get pod webserver-sat-003 -o yaml > 7_webserver-sat-003.yaml
```

Edit `7_webserver-sat-003.yaml`:
- Change `namespace: saturn` → `namespace: neptune`
- Remove `status:` section
- Remove `nodeName:` field
- Remove service account token volumes/mounts

```bash
kubectl -n neptune create -f 7_webserver-sat-003.yaml
kubectl -n saturn delete pod webserver-sat-003 --force --grace-period=0
kubectl get pod -A | grep webserver-sat-003
```

## Solution

```bash
mkdir -p /opt/course/2
kubectl run pod1 --image=httpd:2.4.41-alpine --dry-run=client -oyaml > 2.yaml
```

Edit `2.yaml` and change the container name to `pod1-container`:

```yaml
# 2.yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod1
spec:
  containers:
  - image: httpd:2.4.41-alpine
    name: pod1-container
```

```bash
kubectl create -f 2.yaml
kubectl get pod pod1
```

Write the status command:
```bash
echo 'kubectl -n default describe pod pod1 | grep -i status:' > /opt/course/2/pod1-status-command.sh
# OR using jsonpath:
echo 'kubectl -n default get pod pod1 -o jsonpath="{.status.phase}"' > /opt/course/2/pod1-status-command.sh

sh /opt/course/2/pod1-status-command.sh
```

## Solution

```bash
mkdir -p /opt/course/1
kubectl get ns > /opt/course/1/namespaces
cat /opt/course/1/namespaces
```

The output should look like:
```
NAME              STATUS   AGE
default           Active   Xm
kube-node-lease   Active   Xm
kube-public       Active   Xm
kube-system       Active   Xm
```

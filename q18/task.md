## Task

In Namespace `mars`, the ClusterIP service `manager-api-svc` should make the Pods of Deployment `manager-api-deployment` available inside the cluster, but it's not working.

Test with:
```bash
kubectl -n mars run tmp --restart=Never --rm -i --image=nginx:alpine -- curl -m 5 manager-api-svc:4444
```

Find the misconfiguration and fix it.

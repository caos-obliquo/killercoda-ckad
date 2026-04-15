## Solution

```bash
mkdir -p /opt/course/10
kubectl create namespace pluto 2>/dev/null || true

# Create the pod
kubectl -n pluto run project-plt-6cc-api --image=nginx:1.17.3-alpine --labels project=plt-6cc-api

# Expose it
kubectl -n pluto expose pod project-plt-6cc-api --name project-plt-6cc-svc --port 3333 --target-port 80

# Verify endpoint
kubectl -n pluto describe svc project-plt-6cc-svc

# Test with curl
kubectl run tmp --restart=Never --rm -i --image=nginx:alpine -- curl http://project-plt-6cc-svc.pluto:3333 > /opt/course/10/service_test.html

# Save logs
kubectl -n pluto logs project-plt-6cc-api > /opt/course/10/service_test.log
```

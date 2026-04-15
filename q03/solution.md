## Solution

```bash
kubectl create namespace neptune 2>/dev/null || true
mkdir -p /opt/course/3
kubectl -n neptune create job neb-new-job --image=busybox:1.31.0 --dry-run=client -oyaml -- sh -c "sleep 2 && echo done" > /opt/course/3/job.yaml
```

Edit `/opt/course/3/job.yaml`:
```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: neb-new-job
  namespace: neptune
spec:
  completions: 3
  parallelism: 2
  template:
    metadata:
      labels:
        id: awesome-job
    spec:
      containers:
      - command:
        - sh
        - -c
        - sleep 2 && echo done
        image: busybox:1.31.0
        name: neb-new-job-container
      restartPolicy: Never
```

```bash
kubectl -f /opt/course/3/job.yaml create
kubectl -n neptune get pod,job | grep neb-new-job
kubectl -n neptune describe job neb-new-job
```

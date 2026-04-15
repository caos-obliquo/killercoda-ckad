## Task

Team Neptune needs a Job template located at `/opt/course/3/job.yaml`.

Requirements:
- Image: `busybox:1.31.0`
- Command: `sleep 2 && echo done`
- Namespace: `neptune`
- Total completions: **3**
- Parallel executions: **2**
- Pod label: `id: awesome-job`
- Job name: `neb-new-job`
- Container name: `neb-new-job-container`

Start the Job and check its history.

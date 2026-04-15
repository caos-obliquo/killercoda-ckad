## Task

In Namespace `pluto` there is a single Pod named `holy-api`. Convert it into a Deployment:

- Deployment name: `holy-api`
- Replicas: **3**
- Container security context:
  - `allowPrivilegeEscalation: false`
  - `privileged: false`

The raw Pod template is at `/opt/course/9/holy-api-pod.yaml`.

Save the Deployment yaml to `/opt/course/9/holy-api-deployment.yaml` and delete the original single Pod.

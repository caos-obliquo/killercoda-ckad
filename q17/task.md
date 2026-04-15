## Task

There is a Deployment yaml at `/opt/course/17/test-init-container.yaml` in Namespace `mars`. It spins up a nginx Pod serving files from a mounted volume (currently empty).

Create an **InitContainer** named `init-con`:
- Image: `busybox:1.31.0`
- Mounts the same volume
- Creates `/tmp/web-content/index.html` with content `check this out!`

Test using `curl` from a temporary `nginx:alpine` Pod.

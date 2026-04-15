## Task

There are files at `/opt/course/11/image` to build a container image.

> Run all Docker and Podman commands as root: `sudo docker` / `sudo podman`

1. Change the Dockerfile: set `ENV` variable `SUN_CIPHER_ID` to `5b9c1065-e39d-4a43-a04a-e59bcea3e03f`
2. Build with `sudo docker`, tag as `registry.killer.sh:5000/sun-cipher:v1-docker`, and push
3. Build with `sudo podman`, tag as `registry.killer.sh:5000/sun-cipher:v1-podman`, and push
4. Run a detached container named `sun-cipher` using `sudo podman` with image `v1-podman`
5. Write the container logs to `/opt/course/11/logs`

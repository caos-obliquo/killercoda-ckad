## Solution

```bash
# Step 1: Edit Dockerfile
sudo vim /opt/course/11/image/Dockerfile
# Change/add: ENV SUN_CIPHER_ID=5b9c1065-e39d-4a43-a04a-e59bcea3e03f

# Step 2: Docker build & push
cd /opt/course/11/image
sudo docker build -t registry.killer.sh:5000/sun-cipher:v1-docker .
sudo docker push registry.killer.sh:5000/sun-cipher:v1-docker

# Step 3: Podman build & push
sudo podman build -t registry.killer.sh:5000/sun-cipher:v1-podman .
sudo podman push registry.killer.sh:5000/sun-cipher:v1-podman

# Step 4: Run container
sudo podman run -d --name sun-cipher registry.killer.sh:5000/sun-cipher:v1-podman

# Step 5: Save logs
mkdir -p /opt/course/11
sudo podman logs sun-cipher > /opt/course/11/logs
```

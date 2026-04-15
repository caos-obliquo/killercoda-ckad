## Task

1. Create a PersistentVolume named `earth-project-earthflower-pv`:
   - Capacity: `2Gi`
   - AccessMode: `ReadWriteOnce`
   - HostPath: `/Volumes/Data`
   - No storageClassName

2. Create a PersistentVolumeClaim in Namespace `earth` named `earth-project-earthflower-pvc`:
   - Request: `2Gi`, `ReadWriteOnce`
   - No storageClassName
   - Must bind to the PV

3. Create a Deployment `project-earthflower` in Namespace `earth` of image `httpd:2.4.41-alpine` that mounts the PVC at `/tmp/project-data`.

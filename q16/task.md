## Task

In Namespace `mercury`, there is a Deployment `cleaner` with a container `cleaner-con` that writes logs to `/var/log/cleaner/cleaner.log` via a mounted volume.

The yaml is at `/opt/course/16/cleaner.yaml`.

1. Create a **sidecar container** named `logger-con`, image `busybox:1.31.0`, that mounts the same volume and runs `tail -f /var/log/cleaner/cleaner.log`
2. Save your changes to `/opt/course/16/cleaner-new.yaml` and apply them
3. Check the sidecar logs — what is being removed?

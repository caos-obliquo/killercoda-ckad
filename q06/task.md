## Task

Create a single Pod named `pod6` in Namespace `default` of image `busybox:1.31.0`.

- The Pod should have a **readiness-probe** executing `cat /tmp/ready`
- Initial delay: **5 seconds**
- Period: **10 seconds**
- The Pod should run the command: `touch /tmp/ready && sleep 1d`

Confirm the Pod starts and becomes ready.

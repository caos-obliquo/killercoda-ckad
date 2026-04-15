## Task

In Namespace `moon` there is a nginx Deployment `web-moon` that is waiting for a ConfigMap.

Create a ConfigMap named `configmap-web-moon-html` containing the content of `/opt/course/15/web-moon.html` under the data key `index.html`.

Test the nginx configuration using `curl` from a temporary `nginx:alpine` Pod.

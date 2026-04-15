## Task

Team Pluto needs a new cluster internal Service in Namespace `pluto`:

1. Create a Pod named `project-plt-6cc-api` of image `nginx:1.17.3-alpine` with label `project: plt-6cc-api`
2. Create a ClusterIP Service named `project-plt-6cc-svc` exposing tcp port `3333:80`
3. Use `curl` from a temporary Pod to get the response and write it to `/opt/course/10/service_test.html`
4. Write the Pod logs to `/opt/course/10/service_test.log`

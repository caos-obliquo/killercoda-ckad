## Task

In Namespace `jupiter` there is a Deployment `jupiter-crew-deploy` and a ClusterIP Service `jupiter-crew-svc`.

Change this service to a **NodePort** to make it available on all nodes on port `30100`.

Test the NodePort Service using the internal IP of available nodes on port `30100` using `curl`. On which nodes is the Service reachable?

## Task

In Namespace `moon`, modify the existing Pod `secret-handler`:

1. Create Secret `secret1` with `user=test` and `pass=pwd`; expose as env vars `SECRET1_USER` and `SECRET1_PASS`
2. There is a Secret yaml at `/opt/course/14/secret2.yaml` — create it and mount it inside the Pod at `/tmp/secret2`
3. Save your changes to `/opt/course/14/secret-handler-new.yaml`

Both Secrets should only be available in Namespace `moon`.

## Task

In Namespace `venus` there are two Deployments: `api` and `frontend`, both exposed via Services.

Create a NetworkPolicy named `np1` which:
- Restricts **outgoing TCP connections** from Deployment `frontend`
- Only allows egress to Deployment `api`
- Still allows outgoing traffic on **UDP/TCP port 53** (DNS)

Test using from a Pod of Deployment `frontend`:
```bash
wget www.google.com   # should FAIL
wget api:2222         # should SUCCEED
```

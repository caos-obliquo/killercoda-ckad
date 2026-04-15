## Solution

```bash
# Step 1: Delete the release
helm -n mercury uninstall internal-issue-report-apiv1

# Step 2: Upgrade apiv2
helm repo update
helm search repo nginx --versions
helm -n mercury upgrade internal-issue-report-apiv2 killershell/nginx

# Step 3: Install apache with 2 replicas
helm show values killershell/apache | grep replicaCount
helm -n mercury install internal-issue-report-apache killershell/apache --set replicaCount=2

# Step 4: Find and delete broken release
helm -n mercury ls -a
helm -n mercury uninstall <broken-release-name>
```

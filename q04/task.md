## Task

Team Mercury asked you to perform some operations using Helm, all in Namespace `mercury`:

1. **Delete** release `internal-issue-report-apiv1`
2. **Upgrade** release `internal-issue-report-apiv2` to any newer version of chart `killershell/nginx`
3. **Install** a new release `internal-issue-report-apache` of chart `killershell/apache` with **2 replicas** set via Helm values
4. **Find and delete** a broken release stuck in `pending-install` state

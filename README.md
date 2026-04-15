# CKAD Killer Shell — Killercoda Scenarios

22 practice scenarios based on CKAD Killer Shell exam questions.

## Scenario List

| # | Topic |
|---|-------|
| Q01 | Namespaces |
| Q02 | Pods |
| Q03 | Job |
| Q04 | Helm Management |
| Q05 | ServiceAccount & Secret |
| Q06 | ReadinessProbe |
| Q07 | Pods & Namespaces |
| Q08 | Deployment Rollouts |
| Q09 | Pod to Deployment |
| Q10 | Service & Logs |
| Q11 | Working with Containers |
| Q12 | Storage PV & PVC |
| Q13 | StorageClass & PVC |
| Q14 | Secret Volume & Env |
| Q15 | ConfigMap Volume |
| Q16 | Logging Sidecar |
| Q17 | InitContainer |
| Q18 | Service Misconfiguration |
| Q19 | ClusterIP to NodePort |
| Q20 | NetworkPolicy |
| Q21 | Requests, Limits & ServiceAccount |
| Q22 | Labels & Annotations |

## 🚀 Deploying to Killercoda

### Step 1: Create a GitHub Repo

```bash
# Create a new repo on GitHub (e.g., YOUR_USERNAME/ckad-killercoda)
# Then locally:
git init
git add .
git commit -m "Initial CKAD 22 questions"
git remote add origin https://github.com/YOUR_USERNAME/ckad-killercoda.git
git push -u origin main
```

### Step 2: Connect to Killercoda

1. Go to [killercoda.com/creator/repository](https://killercoda.com/creator/repository)
2. Click **"Add Repository"**
3. Enter: `YOUR_USERNAME/ckad-killercoda`
4. Follow the instructions to add a deploy key and webhook

### Step 3: Access Your Scenarios

Once connected, each scenario will be available at:
```
https://killercoda.com/YOUR_USERNAME/scenario/q01
https://killercoda.com/YOUR_USERNAME/scenario/q02
...
https://killercoda.com/YOUR_USERNAME/scenario/q22
```

## Structure

Each scenario folder contains:
```
qXX/
├── index.json      # Killercoda metadata (title, backend, steps)
├── intro.md        # Introduction shown before the scenario starts
├── task.md         # Step 1: The actual task/question
└── solution.md     # Step 2: Full solution walkthrough
```

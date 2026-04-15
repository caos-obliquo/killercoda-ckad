## Solution

```bash
kubectl create namespace venus 2>/dev/null || true
```

Create `20_np1.yaml`:
```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: np1
  namespace: venus
spec:
  podSelector:
    matchLabels:
      id: frontend
  policyTypes:
  - Egress
  egress:
  - to:
    - podSelector:
        matchLabels:
          id: api
  - ports:
    - port: 53
      protocol: UDP
    - port: 53
      protocol: TCP
```

```bash
kubectl create -f 20_np1.yaml

# Test: external should fail
kubectl -n venus exec <frontend-pod> -- wget -O- -T 5 www.google.com

# Test: internal should work
kubectl -n venus exec <frontend-pod> -- wget -O- api:2222
```

> **Key insight:** Two separate egress rules are OR'd together — one allows traffic to `api` pods, the other allows DNS on port 53.

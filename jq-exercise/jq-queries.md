# JQ Queries

## 1. Get number of replicas from Kubernetes deployment
```bash
jq '.status.replicas' deploy.json

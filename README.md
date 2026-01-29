# Apache Demo - ArgoCD + ORC

Deploy an Apache web server on OpenStack using GitOps.

## Deploy

```bash
kubectl apply -f argocd/application.yaml
```

## Monitor

```bash
kubectl get networks,subnets,routers,ports,servers,floatingips -n orc-system -w
```

## Access

```bash
# Get floating IP
kubectl get floatingip apache-server-fip -n orc-system -o jsonpath='{.status.resource.floatingIP}'

# Web
curl http://<FLOATING_IP>

# SSH
ssh cloud-user@<FLOATING_IP>
```

## Cleanup

```bash
kubectl delete -f argocd/application.yaml
```

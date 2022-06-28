# Install the operator

```bash
oc apply -f openshift-gitops/gitops-operators.yaml
```
# Monitor the operator install
```bash
oc get csv -n openshift-gitops -w
```
# Delete the default app installed by the operator
```bash
oc delete argocd openshift-gitops -n openshift-gitops
```
# Deploy a argocd app with vault plugin
```bash
oc apply -f openshift-gitops/argocd.yaml
```

# Get the route and password of argocd gui
```bash
oc get routes -n openshift-gitops redhat-kong-gitops-server --template='{{ .spec.host }}
```
```bash
oc get secret -n openshift-gitops redhat-kong-gitops-cluster -ojsonpath='{.data.admin\.password}' | base64 -d
```

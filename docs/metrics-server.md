# Metrics Server
cd docs/resources
```
├── cluster.yaml
├── images
│   └── kind-local-docker.jpg
└── metrics-server
    └── components.yaml
```
```
kubectl apply -f metrics-server --validate=false
```
### Output
```
kubectl apply -f metrics-server --validate=false

serviceaccount/metrics-server created
clusterrole.rbac.authorization.k8s.io/system:aggregated-metrics-reader created
clusterrole.rbac.authorization.k8s.io/system:metrics-server created
rolebinding.rbac.authorization.k8s.io/metrics-server-auth-reader created
clusterrolebinding.rbac.authorization.k8s.io/metrics-server:system:auth-delegator created
clusterrolebinding.rbac.authorization.k8s.io/system:metrics-server created
service/metrics-server created
deployment.apps/metrics-server created
apiservice.apiregistration.k8s.io/v1beta1.metrics.k8s.io created
```
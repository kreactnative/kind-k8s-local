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
```
kubectl top nodes
NAME                  CPU(cores)   CPU%   MEMORY(bytes)   MEMORY%   
local-control-plane   347m         2%     711Mi           9%        
local-worker          58m          0%     154Mi           1%        
local-worker2         42m          0%     126Mi           1%       
```
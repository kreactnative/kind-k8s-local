# Test Deploy flutter site
```
├── cluster.yaml
├── flutter
│   └── deployment.yaml
├── images
│   └── kind-local-docker.jpg
├── istio
│   └── istio-operator.yaml
├── istio-gateway.yaml
├── metal-lb
│   ├── configmap.yaml
│   └── metallb.yaml
├── metrics-server
│   └── components.yaml
└── ssl
    ├── _wildcard.local.com-key.pem
    └── _wildcard.local.com.pem
```
### Create deployment/service/virtual service
```
kubectl create ns flutter
kubectl apply -f flutter/deployment.yaml -n flutter
```
### Output
```
namespace/flutter created
service/flutter-test-svc created
deployment.apps/flutter-test created
virtualservice.networking.istio.io/flutter-web-vs created
```
### Get Visual Service
```
kubectl get vs -A
flutter     flutter-web-vs   ["istio-system/local-gateway"]   ["flutter.local.com"]   41s
```
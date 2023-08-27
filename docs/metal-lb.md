# MetalLB
```
├── cluster.yaml
├── images
│   └── kind-local-docker.jpg
├── metal-lb
│   ├── configmap.yaml
│   └── metallb.yaml
└── metrics-server
    └── components.yaml
```
```
kubectl create ns metallb-system
kubectl create secret generic -n metallb-system memberlist --from-literal=secretkey="$(openssl rand -base64 128)"
kubectl apply -f metal-lb --validate=false
```
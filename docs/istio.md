# Istio Service Mesh
```
├── cluster.yaml
├── images
│   └── kind-local-docker.jpg
├── istio
│   └── istio-operator.yaml
├── metal-lb
│   ├── configmap.yaml
│   └── metallb.yaml
├── metrics-server
│   └── components.yaml
└── ssl
    ├── _wildcard.local.com-key.pem
    └── _wildcard.local.com.pem
```
### Install Istio
```
istioctl install -f istio/istio-operator.yaml -y
```
### Output
```
✔ Istio core installed                                                                                                                                                                                     
✔ Istiod installed                                                                                                                                                                                         
✔ Ingress gateways installed                                                                                                                                                                               
✔ Installation complete                                                                                                                                                                         Making this installation the default for injection and validation.
```
### Loadbalancer
```
kubectl get svc -n istio-system
NAME                   TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)                                                    AGE
istio-ingressgateway   LoadBalancer   10.96.77.242    172.19.0.2    15021:30489/TCP,80:31804/TCP,443:30568/TCP,443:30568/UDP   63s
istiod                 ClusterIP      10.96.216.145   <none>        15010/TCP,15012/TCP,443/TCP,15014/TCP                      77s
```
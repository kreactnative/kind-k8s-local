# Istio Gateway
istio-gateway.yaml
```yaml
apiVersion: networking.istio.io/v1beta1
kind: Gateway
metadata:
  name: local-gateway
spec:
  selector:
    app: istio-ingressgateway
    istio: ingressgateway
  servers:
    - port:
        number: 80
        name: http
        protocol: HTTP
      hosts:
        - "*.local.com"
      tls:
        httpsRedirect: true
    - port:
        number: 443
        name: https
        protocol: HTTPS
      hosts:
        - "*.local.com"
      tls:
        mode: SIMPLE
        credentialName: local-cred
```
### Install Gateway
```
kubectl apply -f istio-gateway.yaml -n istio-system
```
### Output
```
gateway.networking.istio.io/local-gateway created
```
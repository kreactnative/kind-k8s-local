# SSL
```
mkcert "*.kind.local"
```
### Output
```
Created a new certificate valid for the following names 📜
 - "*.kind.local"

Reminder: X.509 wildcards only go one level deep, so this won't match a.b.kind.local ℹ️

The certificate is at "./_wildcard.kind.local.pem" and the key at "./_wildcard.kind.local-key.pem" ✅

It will expire on 27 November 2025 🗓
```
### SSL
```
├── _wildcard.kind.local-key.pem
└── _wildcard.kind.local.pem
```
### Create Secret
```
kubectl create ns istio-system
kubectl -n istio-system create secret tls local-cred --key=_wildcard.kind.local-key.pem --cert=_wildcard.kind.local.pem
```
### Outpute
```
namespace/istio-system created
secret/local-cred created
```
### Installing the CA on other systems
```
mkcert -install
```
### Outpute
```
The local CA is already installed in the system trust store! 👍
```
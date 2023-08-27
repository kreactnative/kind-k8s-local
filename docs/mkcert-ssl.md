# SSL
```
mkcert "*.local.com"
```
### Output
```
Created a new certificate valid for the following names 📜
 - "*.local.com"

Reminder: X.509 wildcards only go one level deep, so this won't match a.b.local.com ℹ️

The certificate is at "./_wildcard.local.com.pem" and the key at "./_wildcard.local.com-key.pem" ✅

It will expire on 27 November 2025 🗓
```
### SSL
```
├── _wildcard.local.com-key.pem
└── _wildcard.local.com.pem
```
### Create Secret
```
kubectl create ns istio-system
kubectl -n istio-system create secret tls local-cred --key=_wildcard.local.com-key.pem --cert=_wildcard.local.com.pem
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
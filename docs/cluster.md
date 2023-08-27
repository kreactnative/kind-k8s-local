# Cluster
## Create kind config
### cluster.yaml
```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
name: local
nodes:
- role: control-plane
  kubeadmConfigPatches:
  - |
    kind: InitConfiguration
    nodeRegistration:
      kubeletExtraArgs:
        node-labels: "ingress-ready=true"
  extraPortMappings:
  - containerPort: 80
    hostPort: 80
    protocol: TCP
  - containerPort: 443
    hostPort: 443
    protocol: TCP
  - containerPort: 443
    hostPort: 443
    protocol: UDP
- role: worker
- role: worker
```
### Create cluster
```terminal
kind create cluster --config cluster.yaml
```
### Output
```
~/projects/tutorials/kind-k8s-local/docs/resources  kind create cluster --config cluster.yaml
Creating cluster "local" ...
 ✓ Ensuring node image (kindest/node:v1.27.3) 🖼 
 ✓ Preparing nodes 📦 📦 📦  
 ✓ Writing configuration 📜 
 ✓ Starting control-plane 🕹️ 
 ✓ Installing CNI 🔌 
 ✓ Installing StorageClass 💾 
 ✓ Joining worker nodes 🚜 
Set kubectl context to "kind-local"
You can now use your cluster with:

kubectl cluster-info --context kind-local

Not sure what to do next? 😅  Check out https://kind.sigs.k8s.io/docs/user/quick-start/
```
![docker](resources/images/kind-local-docker.jpg "Docker")
### Get nodes
```
kubectl get nodes -o wide
NAME                  STATUS   ROLES           AGE     VERSION   INTERNAL-IP   EXTERNAL-IP   OS-IMAGE                         KERNEL-VERSION        CONTAINER-RUNTIME
local-control-plane   Ready    control-plane   8m25s   v1.27.3   172.19.0.4    <none>        Debian GNU/Linux 11 (bullseye)   5.15.49-linuxkit-pr   containerd://1.7.1
local-worker          Ready    <none>          8m4s    v1.27.3   172.19.0.3    <none>        Debian GNU/Linux 11 (bullseye)   5.15.49-linuxkit-pr   containerd://1.7.1
local-worker2         Ready    <none>          8m4s    v1.27.3   172.19.0.2    <none>        Debian GNU/Linux 11 (bullseye)   5.15.49-linuxkit-pr   containerd://1.7.1
```
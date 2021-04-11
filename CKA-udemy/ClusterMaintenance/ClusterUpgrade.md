# Manual Cluster Update
## On Control Plane node

```yaml
Current version: 1.19.9
New verion: 1.20.5
Control Plane node:
  - k8s-lab-1
Worker node:
  - k8s-lab-2
Without package manager: true
```

```bash
mkdir binaries && cd binaries
```

```bash
RELEASE="v1.20.5"
```

for latest stable version
```bash
RELEASE="$(curl -sSL https://dl.k8s.io/release/stable.txt)"
```

```bash
sudo curl -L --remote-name-all https://storage.googleapis.com/kubernetes-release/release/${RELEASE}/bin/linux/amd64/{kubeadm,kubelet,kubectl}
```

```bash
sudo chmod +x {kubeadm,kubelet,kubectl}
```


```bash
mv -vf kubeadm /usr/local/bin/kubeadm
```

```bash
kubeadm upgrade plan
```

```bash
kubeadm upgrade apply $RELEASE
```



```bash
mv -vf kubelet /usr/local/bin/kubelet
```

```bash
mv -vf kubectl /usr/local/bin/kubectl
```

```bash
sudo systemctl daemon-reload
sudo systemctl restart kubelet
```


```bash
kubectl get nodes
kubectl drain k8s-lab-2 --ignore-daemonsets
```

## on workers
RELEASE="v1.20.5"

```bash
sudo curl -L --remote-name-all https://storage.googleapis.com/kubernetes-release/release/${RELEASE}/bin/linux/amd64/{kubeadm,kubelet}
```

```bash
sudo chmod +x {kubeadm,kubelet}
```

```bash
sudo mv -vf kubeadm $(which kubeadm)
sudo mv -vf kubelet $(which kubelet)
```


```bash
sudo systemctl daemon-reload
sudo systemctl restart kubelet
```

## on Control Plane
```bash
kubectl uncordon k8s-lab-2
```

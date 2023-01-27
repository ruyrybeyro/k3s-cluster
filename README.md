# k3s-cluster

Raspberry Pi k3s high-availability cluster deployed with Ansible.

Install k3s on primary control-plane:

```shell
echo 'KUBECONFIG=/etc/rancher/k3s/k3s.yaml' >> /etc/environment
install -d /etc/rancher/k3s
cat > /etc/rancher/k3s/config.yaml << 'EOF'
cluster-init: true
disable:
  - local-storage
  - servicelb
disable-cloud-controller: true
node-taint: CriticalAddonsOnly=true:NoExecute
EOF
chown 0600 /etc/rancher/k3s/config.yaml
curl -sfL https://get.k3s.io | sh -s - server
kubectl get nodes -o wide
cat /var/lib/rancher/k3s/server/node-token
```

Install k3s on secondary control-plane:

```shell
echo 'KUBECONFIG=/etc/rancher/k3s/k3s.yaml' >> /etc/environment
install -d /etc/rancher/k3s
cat > /etc/rancher/k3s/config.yaml << 'EOF'
disable:
  - local-storage
  - servicelb
disable-cloud-controller: true
node-taint: CriticalAddonsOnly=true:NoExecute
server: https://apollo.lan:6443
token: K10fff1bfe3cef538a5336dfe9302bec3a2fbae18ae2b4a6603f05f12b95f40b12c::server:de954523bbd2df6482e75a1cd7a0acd7
EOF
chown 0600 /etc/rancher/k3s/config.yaml
curl -sfL https://get.k3s.io | sh -s - server
kubectl get nodes -o wide
cat /var/lib/rancher/k3s/server/node-token
```

Install k3s on worker nodes:

```shell
install -d /etc/rancher/k3s
cat > /etc/rancher/k3s/config.yaml << 'EOF'
node-label:
  - kubernetes.io/role=worker
  - node-type=worker
server: https://apollo.lan:6443
token: K108cd2c40719d2400e34605320405ce9c02b5c3b236105f62332eb84417c6b8e29::server:4ec7de826772a1b408802c4ed01f2484
EOF
chown 0600 /etc/rancher/k3s/config.yaml
curl -sfL https://get.k3s.io | sh -s - agent
```

Set labels for each worker node:

```shell
kubectl label nodes chaos kubernetes.io/role=worker
kubectl label nodes chaos node-type=worker
kubectl label nodes chronos kubernetes.io/role=worker
kubectl label nodes chronos node-type=worker
kubectl label nodes helios kubernetes.io/role=worker
kubectl label nodes helios node-type=worker
```

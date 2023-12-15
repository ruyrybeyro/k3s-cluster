# Cilium

[Cilium](https://github.com/cilium/cilium) is a networking, observability, and security solution with an eBPF-based dataplane.

## Releases

- [Cilium Helm Chart](https://helm.cilium.io)
- [Cilium CLI](https://github.com/cilium/cilium-cli/releases)
- [Cilium Hubble](https://github.com/cilium/hubble/releases)

## Chart Configuration

### [Kubernetes Without kube-proxy](https://docs.cilium.io/en/stable/network/kubernetes/kubeproxy-free/)

For [Cilium #19038](https://github.com/cilium/cilium/issues/19038), k3s does proxy the api server on each host to `localhost:6444`:

```yaml
k8sServiceHost: 127.0.0.1
k8sServicePort: 6444
kubeProxyReplacement: true
```

# Cilium

[Cilium](https://github.com/cilium/cilium) is a networking, observability, and security solution with an eBPF-based dataplane.

- https://luislogs.com/posts/re-engineering-the-homelab-with-iac-and-kubernetes-an-overview/
- https://blog.stonegarden.dev/articles/2023/12/migrating-from-metallb-to-cilium/

## Releases

- [ArtifactHUB](https://artifacthub.io/packages/helm/cilium/cilium)
- [GitHub](https://github.com/cilium/cilium/releases)
- [Cilium CLI](https://github.com/cilium/cilium-cli/releases)
- [Cilium Hubble](https://github.com/cilium/hubble/releases)

## Helm Chart Configuration

- [Reference](https://docs.cilium.io/en/stable/helm-reference/)

### Kubernetes Without kube-proxy

- [Reference](ttps://docs.cilium.io/en/stable/network/kubernetes/kubeproxy-free/)

For [Cilium #19038](https://github.com/cilium/cilium/issues/19038), `k3s` does proxy the API server on each host to `localhost:6444`:

```yaml
k8sServiceHost: 127.0.0.1
k8sServicePort: 6444
kubeProxyReplacement: true
```

Validate the setup:

```shell
sudo kubectl -n kube-system exec ds/cilium -- cilium status --verbose
```

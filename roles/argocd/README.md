# Argo CD

## Releases

- [ArtifactHUB](https://artifacthub.io/packages/helm/argo/argo-cd)
- [GitHub](https://github.com/argoproj/argo-cd/releases)

## Setup

Set `admin` user password:

```shell
ansible-vault encrypt_string '<adminpassword>' --name 'argocd_vars.kubernetes.server.admin.password'
```

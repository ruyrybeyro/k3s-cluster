# ArgoCD

## Releases

- [ArtifactHUB](https://artifacthub.io/packages/helm/argo/argo-cd)
- [GitHub](https://github.com/argoproj/argo-cd/releases)

## Chart Settings

```yaml
argocd_vars:
  server:
    admin:
      password: frontend admin user password
    loadbalancer:
      ip: frontend loadbalancer ip
  version:
    binary: binary version
    chart: chart version
```

Set frontend `admin` user password:

```shell
ansible-vault encrypt_string '<yourpassword>' --name 'argocd_vars.server.admin.password'
```

## Chart Upgrade

```shell
$ ansible-playbook --ask-vault-pass upgrade.yaml --tags argocd
```

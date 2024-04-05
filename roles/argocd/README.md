# Argo CD

## Releases

- [ArtifactHUB](https://artifacthub.io/packages/helm/argo/argo-cd)
- [GitHub](https://github.com/argoproj/argo-cd/releases)

## Setup

Set `admin` user password:

```shell
ansible-vault encrypt_string '<adminpassword>' --name 'argocd_user_password'
```

Login to a controlplane and set `floren` user password:

```shell
argocd login argocd.noty.cc --username admin --password <adminpassword> --insecure
argocd account update-password --account floren --current-password <adminpassword> --new-password <userpassword>
```

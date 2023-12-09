# Longhorn

## Releases

- [Longhorn Helm Chart](https://github.com/longhorn/longhorn/releases)

Uninstall chart:

```shell
kubectl patch lhs deleting-confirmation-flag -n longhorn-system \
    -p '{"value": "true"}' --type=merge 
helm uninstall longhorn -n longhorn-system --wait
kubectl delete namespace longhorn-system
```

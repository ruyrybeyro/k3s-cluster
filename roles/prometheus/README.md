# Prometheus

## Releases

- [kube-prometheus-stack Helm Chart](https://github.com/prometheus-community/helm-charts/releases)

## Uninstall

Uninstall chart:

```shell
helm uninstall monitoring -n monitoring-system --wait
kubectl delete crd alertmanagerconfigs.monitoring.coreos.com
kubectl delete crd alertmanagers.monitoring.coreos.com
kubectl delete crd podmonitors.monitoring.coreos.com
kubectl delete crd probes.monitoring.coreos.com
kubectl delete crd prometheuses.monitoring.coreos.com
kubectl delete crd prometheusrules.monitoring.coreos.com
kubectl delete crd servicemonitors.monitoring.coreos.com
kubectl delete crd thanosrulers.monitoring.coreos.com
kubectl delete secret grafana-credentials -n monitoring-system
kubectl delete namespace monitoring-system
```

# Cluster

Analyze services:

```shell
systemd-analyze blame
```

List dependencies:

```shell
systemctl list-dependencies snapd
systemctl list-dependencies --reverse snapd.socket
```

# Cluster

Cluster related tasks.

## Troubleshooting

Uninstall cloud-init and snapd:

- https://notes.n3s0.tech/posts/20221208145448/
- https://github.com/bodsch/ansible-snapd

Analyze services:

```shell
systemd-analyze blame
```

List package reversed dependencies:

```shell
apt rdepends --installed --recurse git
```

List service dependencies:

```shell
systemctl list-dependencies snapd
systemctl list-dependencies --reverse snapd.socket
```

Firewall state:

```yaml
ufw:
    name: ufw
    source: sysv
    state: running
ufw.service:
    name: ufw.service
    source: systemd
    state: stopped
    status: enabled
```

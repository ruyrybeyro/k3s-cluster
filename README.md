# k3s-cluster

Raspberry Pi k3s high-availability cluster deployed with Ansible.

## Hardware

- 8 x Raspberry Pi 4B with 8GB RAM
- 8 x Samsung PM883 240GB SSD, connected to same USB port
- 8 x SLK Tech [Sata to USB cable](https://www.amazon.com/gp/product/B07S9CKV7X/)
- Unifi [USW-Pro-24-POE](https://store.ui.com/us/en/collections/unifi-switching-pro-power-over-ethernet/products/usw-pro-24-poe) switch, powering the Raspberry Pi's

## Ansible

### Cluster Setup

Install dependencies in MacOS:

```shell
brew install ansible ansible-lint
brew tap esolitos/ipa
brew install esolitos/ipa/sshpass
```

Upgrade [kubernetes.core](https://github.com/ansible-collections/kubernetes.core/blob/main/docs/kubernetes.core.helm_module.rst) [collection](https://docs.ansible.com/ansible/latest/collections_guide/collections_installing.html):

```shell
ansible-galaxy collection install -U kubernetes.core
```

Deploy cluster:

```shell
ansible-playbook --ask-vault-pass provisioning.yaml
```

Reset cluster:

```shell
ansible-playbook --ask-vault-pass reset.yaml
```

### Roles

Each role has their own dedicated README, for additional details and required settings.

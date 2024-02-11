# k3s-cluster

Raspberry Pi k3s high-availability cluster deployed with Ansible.

```shell
brew install ansible ansible-lint
brew tap esolitos/ipa
brew install esolitos/ipa/sshpass
```

Delete successful jobs:

```shell
kubectl delete jobs -A --field-selector status.successful=1
```

## Ansible

Deploy cluster:

```shell
ansible-playbook --ask-vault-pass provisioning.yaml
```

Upgrade [kubernetes.core](https://github.com/ansible-collections/kubernetes.core/blob/main/docs/kubernetes.core.helm_module.rst) [collection](https://docs.ansible.com/ansible/latest/collections_guide/collections_installing.html):

```shell
ansible-galaxy collection install -U kubernetes.core
```

Ignore `ansible-lint` warnings:

```yaml
- name: Disable snapd socket
  ansible.builtin.command:
    cmd: systemctl disable snapd.socket # noqa command-instead-of-module
  changed_when: false
```

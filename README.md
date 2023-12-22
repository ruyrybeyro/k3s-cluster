# k3s-cluster

Raspberry Pi k3s high-availability cluster deployed with Ansible.

```shell
brew install ansible ansible-lint
brew tap esolitos/ipa
brew install esolitos/ipa/sshpass
ansible-playbook -kK provisioning.yaml
```

Delete successful jobs:

```shell
kubectl delete jobs -A --field-selector status.successful=1
```

## Ansible

Ignore `ansible-lint` warnings:

```yaml
- name: Disable snapd socket
  ansible.builtin.command:
    cmd: systemctl disable snapd.socket # noqa command-instead-of-module
  changed_when: false
```

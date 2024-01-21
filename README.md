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

Deploy cluster:

```shell
ansible-playbook --ask-vault-pass provisioning.yaml
```

Upgrade [kubernes.core](https://github.com/ansible-collections/kubernetes.core/blob/main/docs/kubernetes.core.helm_module.rst) [collection](https://docs.ansible.com/ansible/latest/collections_guide/collections_installing.html):

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

Execute task when multiple files are missing:

```yaml
- name: Set binary fact
  ansible.builtin.set_fact:
    binary:
      - name: cilium-cli
        file: cilium
      - name: hubble
        file: hubble

- name: Verify binary files presence
  ansible.builtin.stat:
    path: /usr/local/bin/{{ item.file }}
  loop: '{{ binary }}'
  register: binary_file

- name: Debug
  ansible.builtin.debug:
    msg: "{{ not (binary_file.results | map(attribute='stat.exists')) is all }}"
```

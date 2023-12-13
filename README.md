# k3s-cluster

Raspberry Pi k3s high-availability cluster deployed with Ansible.

```shell
brew install ansible ansible-lint
brew tap esolitos/ipa
brew install esolitos/ipa/sshpass
ansible-playbook -k provisioning.yaml
```

Update the OS distribution:

```shell
ansible-playbook -k distribution.yaml
```

Delete successful jobs:

```shell
kubectl delete jobs --field-selector status.successful=1
```

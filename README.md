# ansible_rancher_k3s

## Configuration

- Change `IPs` in `inventories/${PLATFORM}/hosts` for `${DISTRO}-master` and `${DISTRO}-workers}`.
- Change `K3S_VERSION` in `roles/{k3s-server,k3s-agent}/vars/${DISTRO}-${DISTRO_VERSION}.yaml`

## Install

Run Install command for server and agent:

```
PLATFORM=centos # centos | ubuntu
SSH_USER=centos # centos | ubuntu
ansible-playbook --inventory "inventories/${PLATFORM}/hosts" --user "${SSH_USER}" playbooks/k3s_server_install.yml --extra-vars '{ "hosts": ["centos-masters"] }'
ansible-playbook --inventory "inventories/${PLATFORM}/hosts" --user "${SSH_USER}" playbooks/k3s_server_install.yml --extra-vars '{ "hosts": ["centos-workers"] }'
```

## Uninstall

```
PLATFORM=centos # centos | ubuntu
SSH_USER=centos # centos | ubuntu
ansible-playbook --inventory "inventories/${PLATFORM}/hosts" --user "${SSH_USER}" playbooks/k3s_uinstall.yml --extra-vars '{ "hosts": ["centos-masters"] }'
ansible-playbook --inventory "inventories/${PLATFORM}/hosts" --user "${SSH_USER}" playbooks/k3s_uinstall.yml --extra-vars '{ "hosts": ["centos-workers"] }'
```
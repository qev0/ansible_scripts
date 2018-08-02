# ansible_scripts

### `**Powered by:**`
[![N|Solid](https://upload.wikimedia.org/wikipedia/commons/thumb/2/24/Ansible_logo.svg/195px-Ansible_logo.svg.png)](https://www.ansible.com/)

### Description
Various personally customized ansible scripts for my own personal infrastructure, can be used standalone or in conjuction with [kvm-install-vm](https://github.com/SurrealTiggi/kvm-install-vm/blob/master/kvm-install-vm) and [bootstrap.py](https://github.com/SurrealTiggi/kvm-install-vm/blob/master/bootstrap.py)

### ~/.ansible.cfg

> if using inventory.yml via bootstrap.py then this will already by configured.

```bash
    $ cat ~/.ansible.cfg
    [defaults]
    remote_user=
    host_key_checking = False
    [ssh_connection]
    scp_if_ssh = True
    ssh_args = -o ControlMaster=auto -o ControlPersist=60m
    [privilege_escalation]
    become=True
    become_method=sudo
    become_user=${ANSIBLE_USER}
    become_ask_pass=False
```

> **NOTE!**
> 1. defaults.yml is the default location for various variables that *should* remain encrypted (api keys, ssh keys, config urls, etc)
> 2. It also contains default variables for various roles implemented throughout certain playbooks, documentation for which can be seen via [Ansible Galaxy](https://galaxy.ansible.com)
> 3. Strings encrypted with `ansible-vault encrypt_string --vault-id ${VAULT_FILE} '<string to encrypt>'`

## Convenient way to decrypt on the fly

```bash
$ snap install yq
$ yq read playbook.yml encrypted_value | ansible-vault --vault-id vault-password decrypt
Decryption successful
mysecretstring
```

## Running manually...:

```bash
cd ~/ansible_scripts
ansible-playbook --vault-id ${VAULT_FILE} playbook.yml
```


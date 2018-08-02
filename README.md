# ansible_scripts

### `**Powered by:**`
[![N|Solid](https://upload.wikimedia.org/wikipedia/commons/thumb/2/24/Ansible_logo.svg/195px-Ansible_logo.svg.png)](https://www.ansible.com/)

### Description
Various personally customized ansible scripts for my own personal infrastructure, can be used standalone or in conjuction with [kvm-install-vm](https://github.com/SurrealTiggi/kvm-install-vm/blob/master/kvm-install-vm) and [bootstrap.py](https://github.com/SurrealTiggi/kvm-install-vm/blob/master/bootstrap.py)

### ~/.ansible.cfg
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
    become_user=${YOUR_USER}
    become_ask_pass=False
```

> **NOTE!**
> 1. defaults.yml is the default location for various variables that *should* remain encrypted (api keys, ssh keys, config urls, etc)
> 2. It also contains default variables for various roles implemented throughout certain playbooks, documentation for which can be seen via [Ansible Galaxy](https://galaxy.ansible.com)
> 3. Use `ansible-vault --vault-password-file=${VAULT_FILE}` to decrypt


## Running manually...:

```bash
cd ~/ansible_scripts
ansible-playbook playbook.yml
```


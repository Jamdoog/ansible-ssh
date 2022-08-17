Ansible Role: SSH
=========

An ansible role to install SSH Server & Configure basic users and groups on Debian/Ubuntu, RHEL/CentOS & OpenSUSE systems. 

Requirements
------------

There are no requirements for this role

What this role will do
----------------------

This role will do the following:

- Install the correct openssh-server package for the operating system
- Modify the sudo configuration file and use the "sudo" group
- If provided, create new users with information provided. This can create multiple users
- Modify sshd_config and set sane, secure settings `See variables`


Role Variables
--------------

```yml
NEW_USERS:
  jam:
    groups: "sudo"
    comment: "Ansible"
    shell: "/bin/bash"
    password: ""
    authorized_keys: ""

SUDOERSTEMPLATE: "sudoers"
SSHDTEMPLATE: sshd_config
SSH_SERVER_PACKAGE: "openssh-server"
SSHD_CONFIG: "/etc/ssh/sshd_config"
SSH_DNS: "no"
SSH_EMPTY_PASSWORD: "no"
PASSWORD_AUTHENTICATION: "no"
ROOT_LOGIN: "no"
SSH_PORT: "9030"
SSH_KEY_ROOT: ""
```

Optional variables:

```yml
LISTEN_ADDRESS: {IP}
```

Dependencies
------------

There are no dependencies for this role.

Example Playbook
----------------

```yml
- hosts: ssh
  become: true

  vars:
    NEW_USERS:
      jam:
        groups: "sudo"
        comment: "Ansible"
        shell: "/bin/bash"
        password: ""
        authorized_keys: ""

    SUDOERSTEMPLATE: "sudoers"
    SSHDTEMPLATE: sshd_config
    SSH_SERVER_PACKAGE: "openssh-server"
    SSHD_CONFIG: "/etc/ssh/sshd_config"
    SSH_DNS: "no"
    SSH_EMPTY_PASSWORD: "no"
    PASSWORD_AUTHENTICATION: "no"
    ROOT_LOGIN: "no"
    SSH_PORT: "9030"
    SSH_KEY_ROOT: ""


  roles:
    - role: jamdoog.ssh
```

License
-------

BSD

Author Information
------------------

This role was created by James Ledger, I write about things on https://jamesledger.net

# ansible_pull example
Ansible is generally used to push changes from a server to other hosts.  Ansible-pull runs a playbook (pulls) from a git repo and runs it locally.  It requires ansible to be installed, an entry in the ansible hosts file and a playbook in a git repo to run

## Purpose
How to setup and test ansible pull

## Requirements
ansible  
git

## Description
Below will: 
- uninstall wget
- install ansible, git
- setup the ansible hosts file
- run ansible-pull to reinstall wget

**NOTE:** The raw commands are to simulate a pre-ansible build tool such as [Cloud Formation](https://aws.amazon.com/cloudformation/)

Tested against Amazon Linux ami-c481fad3

### setup:
    --uninstall wget
    sudo yum -y remove wget
    --confirm
    which wget 
    --enable repo and install 
    sudo yum-config-manager --enable epel
    sudo yum -y install ansible git
    --create an entry in ansible hosts file
    sudo sh -c  "echo [local] > /etc/ansible/hosts"; sudo sh -c  "echo 127.0.0.1 >> /etc/ansible/hosts"
    --run ansible pull
    /usr/bin/ansible-pull -U https://github.com/sjdillon/ansible_pull
    --confirm wget was installed
    which wget
    
### output: 
    /usr/bin/ansible-pull -U https://github.com/sjdillon/ansible_pull
    localhost | SUCCESS => {
        "after": "30b9df33ffea8ebc09341473cee99275a239c533",
        "before": "70339e8d7f435272e99798de9b004b10ccd7cd10",
        "changed": true,
        "remote_url_changed": true,
        "warnings": []
    }

    PLAY [local] *******************************************************************

    TASK [setup] *******************************************************************
    ok: [127.0.0.1]

    TASK [install wget] ************************************************************
    ok: [127.0.0.1]

    PLAY RECAP *********************************************************************
    127.0.0.1                  : ok=2    changed=0    unreachable=0    failed=0



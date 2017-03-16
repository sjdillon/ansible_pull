# ansible_pull.yml

Simple yum install to test ansible-pull

#execution
ansible-pull -U https://github.com/sjdillon/ansible_pull

#example
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




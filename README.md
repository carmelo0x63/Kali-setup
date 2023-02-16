# Kali-setup
Ansible playbook to quickly setup a "disposable" Kali Linux VM

----

1. **On the virtualization host**: Download and Deploy (ISO installer)
- ISO file: https://cdimage.kali.org/kali-2022.4/kali-linux-2022.4-installer-amd64.iso
- RAM: 4096, CPU: default
- disk: 24GB
- hostname: <hostname>
- domain: <domain>
- set user name + password
- Software Selection > [continue]

2. **Within the newly created VM**: clone github repo then run playbook
```
$ mkdir github && cd $_

$ git clone https://github.com/carmelo0x99/Kali-setup.git

$ cd Kali-setup

$ virtualenv .

$ source bin/activate

$ python3 -m pip install ansible

$ ansible-playbook kali.yaml -Kv
```

The playbook takes care of the following main tasks:
- APT update + upgrade
- Install: Burpsuite, Docker, Go/golang

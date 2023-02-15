# Kali-setup
Ansible playbook to quickly setup a "disposable" Kali Linux VM

----

1. Download and Deploy
$ curl -LfO https://cdimage.kali.org/kali-2022.4/kali-linux-2022.4-qemu-amd64.7z

$ 7z e kali-linux-2022.4-qemu-amd64.7z

$ sudo mv kali-linux-2022.4-qemu-amd64.qcow2 /var/lib/libvirt/images/

$ sudo chown libvirt-qemu:libvirt-qemu /var/lib/libvirt/images/kali-linux-2022.4-qemu-amd64.qcow2

$ virt-install \
  --name Kali \
  --memory 2048 \
  --vcpus 2 \
  --disk /var/lib/libvirt/images/kali-linux-2022.4-qemu-amd64.qcow2,bus=sata \
  --os-variant generic \
  --network default \
  --print-xml > kali.xml

$ virsh define kali.xml

$ virsh start Kali

2. Basic setup
$ sudo sed -i 's/XKBLAYOUT="en"/XKBLAYOUT="it"/' /etc/default/keyboard

$ sudo timedatectl set-timezone Europe/Rome

3. Clone github repo
$ mkdir github && cd $_

$ git clone https://github.com/carmelo0x99/Kali-setup.git

$ cd Kali-setup

$ virtualenv .

$ source bin/activate

$ python3 -m pip install ansible

$ ansible-playbook kali.yaml -Kv


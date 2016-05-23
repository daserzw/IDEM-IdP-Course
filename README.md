# IDEM-IdP-Course
## Requisiti
vagrant: https://www.vagrantup.com/downloads.html
VirtualBox: https://www.virtualbox.org/wiki/Downloads

## Istruzioni

Clonare il repository:
```git clone https://github.com/daserzw/IDEM-IdP-Course.git```

Avviare vagrant:
```
cd IDEM-IdP-Course
vagrant up
```

Eseguire il playbook di Ansible:
```
vagrant ssh
sudo su
cd /vagrant/ansible
ansible-playbook playbook.yml -i hosts
```

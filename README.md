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
### Ansible chiamato direttamente da vagrant

*NOTA BENE*: quanto segue non e' raccomandato, ovvero deve essere fatto
solo da chi sa quel che fa.

Per chi volesse utilizzare `vagrant provision` e lasciare che vagrant
faccia anche il provisioning c'e' la possibilita' di far chiamare ansible
direttamente tramite il provisione `ansible_local`.
Per abilitare il provisioning tramite `ansible_local` scommentare le
righe seguenti nel *VagrantFile*:

```
#  config.vm.provision :ansible_local do |ansible|
#    ansible.sudo = true
#    ansible.playbook = 'ansible/playbook.yml'
#  end
```


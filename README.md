# IDEM-IdP-Course
## Requisiti

* vagrant: https://www.vagrantup.com/downloads.html
* VirtualBox: https://www.virtualbox.org/wiki/Downloads

## Istruzioni

1. Aprire una finestra di terminale (cmd o powershell su windows).


1. Clonare il repository:
```git clone https://github.com/daserzw/IDEM-IdP-Course.git```

1. Istanziare la macchina virtuale con vagrant
(eseguire nella directory in cui si e' clonato il repository git)

```
cd IDEM-IdP-Course/vagrant
vagrant up
```

1. Provisioning: eseguire il playbook di Ansible
(da eseguire dalla directory del repository: IDEM-IdP-Course)
```
cd vagrant
vagrant ssh
sudo su
cd /vagrant/ansible
ansible-playbook playbook.yml -i hosts
```

1. Aggiungere IdP e SP al proprio hosts file
*Linux/Mac Os X*
```
cd /etc
```

*Windows*
```
cd %SystemRoot%\System32\drivers\etc\
```

*Tutti*
```
echo "10.0.3.2	idp.example.org" >> hosts
echo "10.0.4.2	sp.example.org" >> hosts
```

## Provisioning senza rete
Il primo provisioning della macchina virtuale deve necessariamente essere
effettuato in presenza del collegamento ad Internet. Successivamente, se
si vuole rilanciare ma non eseguendo i task che prevedono il collegamento
si puo' utilizzare il seguente comando:

```
cd /vagrant/ansible
ansible-playbook playbook.yaml -i hosts --skip-tags=online
```

## Ansible chiamato direttamente da vagrant

**NOTA BENE**: quanto segue non e' raccomandato, ovvero deve essere fatto
solo da chi sa quel che fa.

Per chi volesse utilizzare `vagrant provision` e lasciare che vagrant
faccia anche il provisioning c'e' la possibilita' di far chiamare ansible
direttamente tramite il provisioner `ansible_local`.
Per abilitare il provisioning tramite `ansible_local` scommentare le
righe seguenti nel *VagrantFile*:

```
#  config.vm.provision :ansible_local do |ansible|
#    ansible.sudo = true
#    ansible.playbook = 'ansible/playbook.yml'
#  end
```

Il provisioning sara' attivato direttamente con il comando `vagrant up` solo
se e' la prima volta che la macchina virtuale viene istanziata. In seguito
il provisioning e' richiamabile con il comando `vagrant provision`.

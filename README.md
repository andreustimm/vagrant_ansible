# Trabalho Devops e Arquitetura para entrega contínua

## Comandos

### Comandos Vagrant

Comando para subir toda a pilha de servidores

```
vagrant up
vagrant ssh web
vagrant ssh banco
vagrant halt
```

### Comandos Ansible

```
ansible-playbook --private-key=.vagrant/machines/web/virtualbox/private_key -u vagrant -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory ansible/lamp.yml
ansible web -u vagrant --private-key .vagrant/machines/web/virtualbox/private_key -i ansible/hosts -m ping
ansible banco -u vagrant --private-key .vagrant/machines/banco/virtualbox/private_key -i ansible/hosts -m ping
```

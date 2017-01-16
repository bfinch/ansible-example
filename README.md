Example Ansible Project
=======================

An example ansible project organized by splitting up servers by environment and role. Different environments are each separated into their own inventory files.  (dev vs prod) and server types are differentiated by inventory groups and roles. Assumes RHEL based servers using yum. You can spin up a set of Centos 7 servers using vagrant up, then add them to your ssh config using 

```
vagrant ssh-config >> $HOME/.ssh/config
```

## Examples 

### Apply the webserver role to all webserver hosts in dev 

```
ansible-playbook -i inventories/dev webserver.yml
```

### Apply the database role to all database hosts in prod 

```
ansible-playbook -i inventories/prod database.yml 
```

### Apply the common role to all hosts in both dev and prod 

```
ansible-playbook -i inventories common.yml
```

### Check that all webserver hosts in dev are in sync with the role definition. Do not make changes

```
ansible-playbook -i inventories/dev webserver.yml --check
```

### Run an adhoc query to check if the package java is installed against prod servers 

```
ansible all -i inventories/prod -m yum -a "name=java state=present" --check
```



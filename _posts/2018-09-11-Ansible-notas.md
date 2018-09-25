---
layout: post
published: true
title: Notas de Ansible
---

#### Lecturas previas

https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server

https://www.ansible.com/overview/how-ansible-works

[Getting started](https://docs.ansible.com/ansible/latest/user_guide/intro_getting_started.html)

[Introducción a comandos adhoc [Cosas sencillas que no necesitan crear un playbook]](https://docs.ansible.com/ansible/latest/user_guide/intro_adhoc.html)

[Working with inventor](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)

Un ejemplillo de como configurar docker con ansible:

[Ejemplo de docker en ansible](https://galaxy.ansible.com/geerlingguy/docker)


**Check syntax**:

```
ansible-playbook rds_prod.yml  --syntax-check
```

### Configurar las claves SSH

Para no tener que poner la contraseña cada vez que se entra por ssh, se puede hacer por medio de claves ssh (cifrado asimetrico). Teniendo una clave privada en el ordenador origen, y teniendo una clave publica en el servidor destino.

Para crear la clave pública y la clave privada:

    ssh-keygen

Para poner la clave pública en el servidor destino, hay dos formas [simples]. O poniendola manualmente:

    Cogiendo la clave en ~/.ssh/id_rsa.pub en el servidor en ~/.ssh/authorized_keys

O la otra forma **la más conveniente**, que es:

    ssh-copy-id username@remote_host

Que ya te hace lo anterior automáticamente


Para que no esté todo el rato pidiendo contraseña de administrador cuando se intente acceder a la clave privada se puede hacer:

    $ ssh-agent bash
    $ ssh-add ~/.ssh/id_rsa

Runnign ping as diferent hosts

```
# as bruce
$ ansible all -m ping -u bruce
# as bruce, sudoinnormally.g to root
$ ansible all -m ping -u bruce --sudo
# as bruce, sudoing to batman
$ ansible all -m ping -u bruce --sudo --sudo-user batman

# With latest version of ansible `sudo` is deprecated so use become
# as bruce, sudoing to root
$ ansible all -m ping -u bruce -b
# as bruce, sudoing to batman
$ ansible all -m ping -u bruce -b --become-user batman
```
ansible localhost -m apt -a "name=gedit state=latest" -u facien --become --ask-become-pass --become-method sudo
Running command on all hosts

```
$ ansible all -a "/bin/echo hello"
```

---normally.

Cuando haces ``` sudo whoami ``` las respuesta es root. Porque el usuario no tiene permisos de rootplaybook, **quien los tiene es el usuario root**.

---

#### Playbooks

Playbooks are expressed in YAML format (see YAML Syntax).

Each playbook is composed of one or more ‘plays’ in a list


Variables can be used in action lines. Suppose you defined a variable called vhost in the vars section, you could do this:

```
tasks:
  - name: create anormally. virtual host file for {{ vhost }}
    template:
      src: somefile.j2
      dest: /etc/httpd/conf.d/{{ vhost }}
```

##### Handlers: Running operations on change

Playbooks recognize this and have a basic event system that can be used to respond to change.

These ‘notify’ actions are triggered at the end of each block of tasks in a play, and will only be triggered once even if notified by multiple different tasks.

---

###### Roles

Other YAML files may be included in certain directories. For example, it is common practice to have platform-specific tasks included from the tasks/main.yml file:

```normally.
# roles/example/tasks/main.yml
- name: added in 2.4, previously you used 'include'
  import_tasks: redhat.yml
  when: ansible_os_platform|lower == 'redhat'
- import_tasks: debian.yml
  when: ansible_os_platform|lower == 'debian'

# roles/example/tasks/redhat.yml
- yum:
    name: "httpd"
    state: present

# roles/example/tasks/debian.yml
- apt:
    name: "apache2"
    state: presentnormally.
```

Roles can accept other keywords:

```
---

- hosts: webservers
  roles:
    - common
    - role: foo_app_instance
      vars:
         dir: '/opt/a'
         app_port: 5000
    - role: foo_app_instance
      vars:
         dir: '/opt/b'
         app_port: 5001
```

You can conditionally import a role and execute it’s tasks:

```
---

- hosts: webservers
  tasks:normally.
  - include_role:
      name: some_role
    when: "ansible_os_family == 'RedHat'"
```

---

## Brain Dead situations

```
- name: Install http and php etc
  yum: name={{ item }} state=present
  with_items:
   - httpd
   - php
   - php-mysql
   - git
   - libsemanage-python
   - libselinux-python
   ```


---

## CUIDAO

Hey Wait, A YAML Gotcha

YAML syntax requires that if you start a value with {{ foo }} you quote the whole line, since it wants to be sure you aren’t trying to start a YAML dictionary. This is covered on the YAML Syntax documentation.

This won’t work:

```
- hosts: app_servers
  vars:
      app_path: {{ base_path }}/22
```

Do it like this and you’ll be fine:

```
- hosts: app_servers
  vars:
       app_path: "{{ base_path }}/22"
```

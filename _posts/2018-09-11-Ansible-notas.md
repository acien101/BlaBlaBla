---
layout: post
published: true
title: Notas de Ansible
---

#### Lecturas previas

https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server

https://www.ansible.com/overview/how-ansible-works

https://docs.ansible.com/ansible/latest/user_guide/intro_getting_started.html

https://docs.ansible.com/ansible/latest/user_guide/intro_adhoc.html

Un ejemplillo de como configurar docker con ansible:

https://galaxy.ansible.com/geerlingguy/docker



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

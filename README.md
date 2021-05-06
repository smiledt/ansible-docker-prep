Docker-Prep
=========

This role installs docker on my Ansible hosts. It uses several roles from Ansible-Galaxy to do this. Most notably, it uses some of [Jeff Geerling](https://github.com/geerlingguy)'s roles.

Requirements
------------

These roles must be installed from Ansible-Galaxy. See requirements.yml.

Role Variables
--------------

Required variables are listed here, along with default example values. See defaults/main.yml. Any of these defaults can be overwritten by using the vars role directory. 

    docker_users:
      - foo
      - bar

These are the users to be added to the docker group.

Dependencies
------------

None.

Example Playbook
----------------

    - name: Install docker and docker-compose on docker hosts.
      hosts: docker
      become: true
      vars:
        pip_install_packages:
          - name: docker
    
      roles:
        - geerlingguy.pip
        - geerlingguy.docker
    
    - name: Prep the docker hosts.
      hosts: docker
      become: true
      roles:
      - role: docker-users
      - role: calvinbui.ansible_docker_network

This playbook installs docker on the container, then configures the docker network. 

License
-------

BSD

Author Information
------------------

Derek Smiley - Aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/
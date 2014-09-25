LAMP stack on Vagrant CentOS virtual machine with Ansible
=========================================================
This Repository contains scripts that deploy LAMP stack into a CentOS Vagrant virtual machine.

## Requirements

* [Vagrant](http://vagrantup.com)
* [Ansible](http://ansible.github.com)aa_

## Setup

- Install Ansible

  - with pip
  
  ```
  pip install ansible
  ```
  
  - with homebrew (for Mac users)
  
  ```
  brew install ansible
  ```
  
  - with yum
  
  ```
  yum install ansible
  ```
  
  - with apt-get
  
  ```
  apt-get install ansible
  ```

- Install dependency

```
$ git clone https://github.com/shufo/ansible-redhat-lamp
$ cd ansible-redhat-lamp
$ ansible-galaxy install --roles-path=provisioning/roles bennojoy.memcached geerlingguy.apache geerlingguy.mysql geerlingguy.ntp geerlingguy.php geerlingguy.php-mysql geerlingguy.redis geerlingguy.repo-epel geerlingguy.repo-remi
```

- Set your environment

edit ```provisioning/vars/main.yaml```
```
project_name: "example"
target_domain: "example.local.com" // this is your access point
```

- Build Vagrant virtual machine

```
$ vagrant up
```

- Place your project to this folder

- Now you can access project at http://example.local.com/
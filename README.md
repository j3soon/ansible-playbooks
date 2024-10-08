# Ansible Playbooks

Most of the scripts are only tested on Ubuntu (amd64), and may require changes when running on other distros.

## Setup

Clone this repository:

```sh
git clone https://github.com/j3soon/ansible-playbooks.git
cd ansible-playbooks
```

[Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html#installing-ansible-on-ubuntu) on local host:

```sh
sudo apt update
sudo apt install -y software-properties-common
sudo add-apt-repository -y --update ppa:ansible/ansible
sudo apt install -y ansible
```

Set up OpenSSH server and Copy SSH Key on the remote hosts by following [this post](https://tutorial.j3soon.com/remote-development/openssh-server/).

## Basics

```sh
ansible-playbook --ask-become-pass -i inventory setup-dev-env.yaml
```

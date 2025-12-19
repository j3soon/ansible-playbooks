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

and create an inventory file (replace `<TARGET_HOST_IP_*>` with the IP addresses of the target hosts):

```sh
cat <<EOF > inventory
[dev]
<TARGET_HOST_IP_1>
<TARGET_HOST_IP_2>
EOF
```

Set up OpenSSH server and Copy SSH Key on the remote hosts by following [this post](https://tutorial.j3soon.com/remote-development/openssh-server/).

## Basics

For x86:

```sh
ansible-playbook --ask-become-pass -i inventory setup-pc-dev-env.yaml
```

For Jetson:

```sh
ansible-playbook --ask-become-pass -i inventory setup-jetson-dev-env.yaml
```

For DGX Spark:

```sh
ansible-playbook --ask-become-pass -i inventory setup-dgx-spark-dev-env.yaml
```

For Local (need to comment out all unnecessary tasks):

```sh
# Note that this will install everything on the current local host.
ansible-playbook --ask-become-pass -i inventory setup-pc-dev-env.yaml --connection=local
```

## Debug

```sh
ansible-playbook --ask-become-pass -i inventory setup-pc-dev-env.yaml -vvvv
```

If strange issue occurs, consider upgrading the local host:

```sh
sudo apt-get upgrade
```

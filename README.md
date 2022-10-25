# ansible-nextcloud

Ansible playbook to deploy a Nextcloud 24 instance on a clean 22.04 Ubuntu server (LEMP PHP 8.1 stack)

## Prerequisites

A clean Ubuntu 22.04 instance with root/sudo access.

## Create a VM on Scaleway

### Prerequisites

* Generate an SSH key pair (called admin.key and admin.pub)
* Put them on the remote host
* Install prerequisites system packages

```bash
sudo apt-get install python3 python3-dev python3-pip build-essential libssl-dev libffi-dev jq
```

* Install Python packages on the local machine

```bash
pip3 install jinja2 PyYAML paramiko cryptography packaging
```

* Install Ansible (ideally from sources, as it evolves really fast)

If you don't want to install it from sources, you can use the PPA (see Ansible documentation)

```bash
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

## Install Nextcloud

### DNS resolution

With the Ubuntu 22.04 available with a public IP, it's important to choose a DNS name for your future nextcloud service.

Use a DNS name provider to add a IPv4/6 A/AAAA record to map this DNS name to your server IP.

### Installation

Now that you have a working Ubuntu 22.04 available and resolvable, you can either run the installation playbook from your local machine to install on the distant server or directly from the future Ubuntu Nextcloud server.

```bash
ansible-playbook -i your_inventory.yml nextcloud_install.yml
```

The playbook will prompt you for variables like password or DNS names. Store them for future use.

### Result

## TODO

* Automate Lets Encrypt certificate DNS challenge 

## Sources

* [github.com/felixfontein/acme-certificate](https://github.com/felixfontein/acme-certificate)

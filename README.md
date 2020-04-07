# ansible-nextcloud

Ansible playbook to deploy a Nextcloud instance on a clean 18.04 Ubuntu server (LEMP PHP7.2 stack)

## Prerequisites

A clean Ubuntu 18.04 instance with root access. If you don't have one, follow the next chapter to deploy a clean Ubuntu 18.04 instance on Scaleway (costs less than 4€ a month, payed hourly). If you already have one, skip the following "Create a VM on Scaleway" chapter.

## Create a VM on Scaleway

### Prerequisites for Scaleway VM

* Create an account in Scaleway
* Generate an SSH key pair (called admin.key and admin.pub)
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

### Scaleway token

Create a token in Scaleway to authenticate Ansible access to the Scaleway API. In this repo, an empty environment file has been create with the name `scaleway_token`. Add you token in it and should look like this:

```bash
export SCW_API_KEY='aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa'
```

Source the file

```bash
source scaleway_token
```

### Create a VM

Use scaleway\_create\_vm.yaml to:

* get organisation id of the Scaleway account
* find a compatible Ubuntu image for the VM
* add the admin SSH key if necessary
* create the VM itself

```bash
ansible-playbook scaleway_create_vm.yml
```

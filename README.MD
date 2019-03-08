# Ansible playbooks for GitLab runner

* Docker
* GitLab Runner

## Getting started

### Supported distributions

* Ubuntu Trusty
* Debian (Not tested)

Other versions of the distributions listed above might work, but no guarantees given.

### Installing Ansible
You can install Ansible by following the [official installation documentation](http://docs.ansible.com/ansible/intro_installation.html). For Windows 10 users, you can use the instructions for Ubuntu after [installing the Linux subsystem](https://msdn.microsoft.com/en-us/commandline/wsl/install_guide). For older Windows version, please [check this tutorial on running Ansible on cygwin](https://www.jeffgeerling.com/project/running-ansible-within-windows).

### Clone the repository
```shell
git clone git@github.com:Rishats/ansible_gitlab_runner.git
```

### Configure your inventory files
The inventory files are located in the inventory directory. Check the example for development and read the [Ansible documentation](http://docs.ansible.com/ansible/intro_inventory.html).

### Configure your host variables
Host variables control some of the aspects how the machine is configured. Store the host variable file with the same name as the hostname in the inventory file. Below is an example for the production development machine. 

```yaml


```

### Install
1) git clone project.
2) create file gitlab_runner in host_vars and paste data above.
3) python3 -m venv env
4) source env/bin/activate
5) pip install -r requirements.txt
6) ansible -i inventory/production servers -m ping
7) ansible-playbook -i inventory site.yml

### Securing your host variables
Since you storing highly confidential information like production database passwords in the host variables and .env templates it is highly recommend that encrypt them with a symmetric AES key. Luckily Ansible has built-in tool for this called Vault. Please [read the Vault documentation](http://docs.ansible.com/ansible/playbooks_vault.html) on how to set it up.

#### Supported variables

## Running

### Checking SSH access
After you have done with the configuration make sure you have SSH access to the servers that listed on the inventory file. You can test this by using the ping module. Troubleshooting the SSH connection is the out of scope of this repository. Please note that you can set the SSH user and port in the inventory file, see the development for example.

```shell
ansible -i inventory/production servers -m ping
localhost | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

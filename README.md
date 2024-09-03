# Create Linux Distros Using Vagrant and Ansible
The [Vagrantfile](./Vagrantfile) and Ansible [playbook.yml](./playbook.yml) files in this repository create a multi-machine Virtual Box environment with Rocky, Debian, Ubuntu, and openSUSE boxes.

## Description
Once instantiated, the Vagrantfile reads a list containing the custom machine settings for four (4) Vagrant boxes:

+ bento/rockylinux-9.4
+ bento/ubuntu-24.04
+ bento/debian-12.6
+ bento/opensuse-leap-15.6

In addition to the Vagrant box name, the custom machine settings include a hostname, private IP address, and host SSH port.

The hostname value is also applied as the VirtualBox name. Custom values are also provided for the VirtualBox memory, cpus, and gui options.

For each box, the Vagrant Ansible Local provisioner executes [playbook.yml](./playbook.yml). This playbook upgrades the packages each machine to the latest versions.

## Getting Started

### Dependencies

Vagrant and the VirtualBox provider must be installed on the host machine. While Vagrant does support other providers, such as VMware and Hyper-V, the [Vagrantfile](./Vagrantfile) in this repository is written specifically for VirtualBox.

### Installation
To install the files, clone the [vagrant-linux-distros](.) repo or download the files to a folder on the local host.

## Usage
Using the CLI on the host machine, navigate to the folder where the files are located.  To create the machines, run the following:

```bash
vagrant up
```

To stop the machines and destroy all resources:

```bash
vagrant destroy
```

## License
Licensed under the [GNU General Public License v3.0](./LICENSE).

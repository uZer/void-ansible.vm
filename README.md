## [theVoid-infrastructure] ansible.vm

Ansible ESXi management to create and manipulate virtual machines on good old
VMWare ESXI Hypervisors. Builds CoreOS cloud-config volumes for VMWare usage.
Relies on DHCP and CoreOS vmx preconfiguration (should be included here for
the last part).

Work in progress, should be outdated quickly.

#### Install and Usage
Install Ansible and VMWare libs.
See [access-tower] profile in void-ansible.app

    $ git clone https://github.com/uZer/void-ansible.vm.git ~/void-ansible.vm
    $ cat >> ~/.zshrc < EOF
    playvm() {
        cd ~/void-ansible.vm
        ansible-playbook site.yml \
            --vault-password-file ~/.vault_pass
            -D -i inventories/all-prod -l $@
    }
    EOF
    $ playvm esxi01.void -vvvv
    $ playvm esxi01.void

#### Security concerns

This repository contains a script that builds a "cloud-config repository" :
a folder that will contain each cloud-config of each CoreOS, including etcd2
discovery URL. This URL is stored in a vault file. The built repository should
not be uploaded


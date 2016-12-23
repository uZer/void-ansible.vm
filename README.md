## THEVOID INFRASTRUCTURE: ansible.vm

Ansible ESXi management to create and manipulate virtual machines on good old
VMWare ESXI Hypervisors.

#### Requirements

Ansible and VMWare libs.
See [tower] profile in ansible.app

#### Install and Usage


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



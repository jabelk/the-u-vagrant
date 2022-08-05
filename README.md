# The U Vagrant


tested with Vagrant 2.2.14 and virtualbox 6.1.34 on OS X 12.5


`vagrant up` will pull down the Ubuntu 20.04 image and provision with the `build-vm.yml` playbook pulling in each of the Ansible roles listed. 

**note** the `ubuntu-desktop` package randomly inconsistently fails when installing. Re-run the provision step with `vagrant provision` to try again.
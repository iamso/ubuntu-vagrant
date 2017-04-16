Vagrantfile
===========

My default Vagrantfile for spinning up Ubuntu VMs.

Usage
-----

Copy the file to the folder where you want to create the VM, open the folder in Terminal and enter `vagrant up`. After that enter `vagrant ssh` to connect to the VM through SSH.

Options
-------

Check the Vagrantfile for the available options. Set the options as ENV variables.

```bash
BOX_DOMAIN=mydomain.tld vagrant up
```

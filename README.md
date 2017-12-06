# Vagrant Ubuntu

Basic Ubuntu LAMP stack.

Download as a zip to get the needed files ([`Vagrantfile`](Vagrantfile) and [`bootstrap.sh`](bootstrap.sh)). Put these files in a directory and run `vagrant up`.

Before provisioning, don’t forget to edit these things:

1. `DOCUMENT_ROOT`, `SERVER_NAME` and `DATABASE_NAME` at the top of [`bootstrap.sh`](bootstrap.sh)
1. Optionally, the IP address `192.168.100.100` in [`Vagrantfile`](Vagrantfile).

## Vagrant tips

Here’s a few useful commands:

```bash
# Start VM:
$ vagrant up
# Reload, no provision:
$ vagrant reload
# Reload and provision:
$ vagrant reload --provision
# SSH into VM:
$ vagrant ssh
# Stop VM:
$ vagrant halt
```

When running `vagrant up`, Vagrant will install dependencies as defined by the provisioning script(s); this is called “[Automatic Provisioning](https://www.vagrantup.com/intro/getting-started/provisioning.html)”.

If you make any modifications to the [`Vagrantfile`](Vagrantfile), `reload` should be called.

If you make changes to your `Vagrantfile`’s provisioner’s (i.e., [`bootstrap.sh`](bootstrap.sh)), you’ll want to call `reload --provision`.

A full list of Vagrant’s CLI commands can be found here: [Command-Line Interface](https://www.vagrantup.com/docs/cli/).

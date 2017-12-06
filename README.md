# Vagrant LAMP

Basic Ubuntu LAMP stack. macOS-centric.

## Usage

Manually [Install Vagrant](https://www.vagrantup.com) and [VirtualBox](https://www.virtualbox.org/wiki/Downloads). **OR**, for macOS users, install using [Homebrew](https://brew.sh/):

```bash
$ brew cask install virtualbox vagrant vagrant-manager
# Bonus! Use this to update previously installed casks:
$ brew cask outdated | xargs brew cask reinstall
```

Create a directory for your Vagrant projects; I put mine here:

```text
~/dev/vagrant/<name of project>
```

Install the necessary files ([`Vagrantfile`](Vagrantfile) and [`bootstrap.sh`](bootstrap.sh)):

1. Download as a [`zip`](../../archive/master.zip).
1. Clone it: `$ git clone https://github.com/mhulse/vagrant-lamp.git`.
1. Fork it and clone: `$ git clone git@github.com:<username>/vagrant-lamp.git`.

As a convenience to **macOS** users, from the command line, navigate to `vagrant/<name of project>` directory and run:

```bash
$ bash <(curl -sL )
```

Next, edit these settings:

1. `DOCUMENT_ROOT`, `SERVER_NAME` and `DATABASE_NAME` at the top of [`bootstrap.sh`](bootstrap.sh)
1. Optionally, the IP address `192.168.100.100` in [`Vagrantfile`](Vagrantfile).

Finally, from within your project directory, run:

```bash
$ vagrant up
```

Once the VM is up, you can ssh into the current running Vagrant box:

```bash
$ vagrant ssh
```

You are now connected to the Vagrant box at `/home/vagrant`.

Use this to disconnect:

```bash
$ logout
```

… and then this when you are done developing:

```bash
# Terminate the use of any resources by the virtual machine:
$ vagrant destroy
```

**Note:** The vagrant destroy command does not actually remove the downloaded box file. To completely remove the box file, you can use the `vagrant box remove` command.

## VirtualHost

On your host machine, edit your hosts file so that it points to the IP address found in [`Vagrantfile`](Vagrantfile) (default: `192.168.100.100`) and the server name defined at the top of [`bootstrap.sh`](bootstrap.sh) (default: `example.local`).

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
# See what is running:
$ vagrant global-status
```

When running `vagrant up`, Vagrant will install dependencies as defined by the provisioning script(s); this is called “[Automatic Provisioning](https://www.vagrantup.com/intro/getting-started/provisioning.html)”.

If you make any modifications to the [`Vagrantfile`](Vagrantfile), `reload` should be called.

If you make changes to your `Vagrantfile`’s provisioner’s (i.e., [`bootstrap.sh`](bootstrap.sh)), you’ll want to call `reload --provision`.

A full list of Vagrant’s CLI commands can be found here: [Command-Line Interface](https://www.vagrantup.com/docs/cli/).

---

Copyright © 2017 [Michael Hulse](http://mky.io).

Licensed under the Apache License, Version 2.0 (the “License”); you may not use this work except in compliance with the License. You may obtain a copy of the License in the LICENSE file, or at:

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an “AS IS” BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

<img src="https://github.global.ssl.fastly.net/images/icons/emoji/octocat.png">

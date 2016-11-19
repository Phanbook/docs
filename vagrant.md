# Phanbook Developer Install Guide (Vagrant)


The following instructions will automatically download and provision a virtual machine for you to begin hacking
on Phanbook with:

### Getting Started

1. Install Git: http://git-scm.com/downloads (or [GitHub for Windows](http://windows.github.com/) if you want a GUI). Recommend use github for Windows
2. Install VirtualBox: https://www.virtualbox.org/wiki/Downloads
3. Install Vagrant: http://www.vagrantup.com/ (We require Vagrant 1.7.2 or later)
4. Open a terminal and clone the project: `git clone https://github.com/phanbook/opsfiles.git`
5. Enter the project directory: `cd opsfiles` (Recommendation Create your workspace directory and clone project there. C:/workspace/opsfiles/)

### Using Vagrant

When you're ready to start working, boot the VM:

```
chmod +x run && ./run up
```
Or you can runninng via command below

```
vagrant up
```

Vagrant will prompt you for your admin password. This is so it can mount your local files inside the VM for an easy workflow.

(The first time you do this, it will take a while as it downloads the VM image and installs it. Go grab a coffee.)

**Note to Linux users**: Your Phanbook directory cannot be on an ecryptfs mount or you will receive an error: `exportfs: /home/your/path/to/Phanbook does not support NFS export`

**Note to OSX/Linux users**: Vagrant will mount your local files via an NFS share. Therefore, make sure that NFS is installed or else you'll receive the error message:

```
Mounting NFS shared folders failed. This is most often caused by the NFS
client software not being installed on the guest machine. Please verify
[...]
```

For example, on Ubuntu, you can install NFS support by installing nfs-kernel-server with

``` sudo apt-get install````

Once the machine has booted up, you can connecting shell the machine that by typing:

```
./run ssh
```
Or via 

```
vagrant ssh
```

The Phanbook code is found in the /usr/share/nginx/html/www directory in the image.

**Note to Windows users**: You cannot run ```vagrant ssh``` from a cmd prompt; you will receive the error message like below:

```
`vagrant ssh` isn't available on the Windows platform. You are still able
to SSH into the virtual machine if you get a Windows SSH client (such as
PuTTY). The authentication information is shown below:

Host: 192.168.33.33
Port: 2222
Username: vagrant
Private key: C:/Users/Your Name/.vagrant.d/insecure_private_key
```

At this point, you will want to get an SSH client, and use it to connect to your Vagrant VM instead. We recommend [PuTTY Download Link](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

You may use this client to connect to the VM by using ```vagrant/vagrant``` as your username/password, or by [using
PuTTYGen to import the insecure_private_key file](http://jason.sharonandjason.com/key_based_putty_logins_mini_how_to.htm)
(mentioned above) into a PuTTY profile to quickly access your VM.


### Let's contribution for phanbook.
1. checkout your new branch (feature/your-name-branch)

```
$ ## creating new branch
$ git checkout -b feature/{your-new-branch-name}
```
2. commit your files and let's push

```
git push origin feature/{your-new-branch-name}
```

### Shutting down the VM

When you're done working on Phanbook, you can shut down Vagrant with:

```
vagrant halt
```

or you can running 

```
./run halt
```

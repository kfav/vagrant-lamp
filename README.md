# vagrant-lamp-bootstrap

A super-simple Vagrantfile / bootstrap.sh to setup a LAMP stack inside Vagrant automatically.

### What ?

This is a reduced-to-the-max Vagrant setup file for a quick development stack. It will:

* setup a Ubuntu 14.04 LTS "Trusty Tar" 64bit box

* make the box accessable by the host at IP localhost or `127.0.0.1` port 80. 
- or - change the host port to whatever you like or even use a private network address ip by adding the line:
config.vm.network "private_network", ip: "192.168.33.22"

and deleting the line:
config.vm.network "forwarded_port", guest: 80, host: 80

* syncs the local "sites" folder with `/var/www/html` inside the box 
- or - change to sync the current folder "./" with '/var/www/html' inside the box.

* automatically performs all the commands in bootstrap.sh directly after setting up the box for the first time

The bootstrap.sh will:

* update, upgrade

* create a folder inside /var/www/html

* install apache 2.4, php 5.5, MySQL, PHPMyAdmin, git and Composer

* sets a pre-chosen password for MySQL and PHPMyAdmin

* activate mod_rewrite and add *AllowOverride All* to the vhost settings

* adds the php index file to the first position of dir.conf

You can change the folder and password inside the bootstrap.sh file.

### How to use ?

Put `Vagrantfile` and `bootstrap.sh` inside a folder and do a `vagrant up` on the command line.
This box uses Ubuntu 14.04 LTS "Trustry Tar" 64bit, so if you don't have the basic box already, do `vagrant box add ubuntu/trusty64`.

### Why ?

Personal time-saving bootstrap for Vagrant, it might be useful for you too.

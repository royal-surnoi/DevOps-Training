## SSH - Secure Shell

it is a network protocol that allows two computers to communicate and share data over an encrypted connections,it is used to log in to and perform operations in remote server in secure way.

command ro generate SSH keys in local server

` ssh key-gen -f royal`

based on file two name files will be generated 

`royal` `royal.pub`

![ley-lock](https://www.pngitem.com/pimgs/m/313-3139000_icon-key-lock-clipart-png-download-transparent-png.png)


> to connect remove servers we need to share public key `royal.pub` only and the key need to store .ssh/authorized_keys and provide user to executable permissions then only you can connect.

command to connect remote server through SSH

`ssh -i <privatekey_file_location> <user_name>@<public_IP>`

`ssh -i royal.pem ec2-user@100.1.25.6`

---

## Basic Linux Commands
> How to find normal user / root user immediately

1. `#` - root
2. `$` - normal user`

## Set Hostname in the server
``` bash
# Debian/Ubutu
#!/bin/bash

# Setup Hostname
sudo hostnamectl set-hostname "userserver"

# Update the hostname part of Host File
echo "`hostname -I | awk '{ print $1 }'` `hostname`" >> /etc/hosts
```
## OS and Kernal
![OS-Kernal](https://www.tutorialspoint.com/operating_system/images/linux_os.jpg)
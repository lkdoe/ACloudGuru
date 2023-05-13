# Setting up ansible
## Installation
### On Ubuntu: 
```
apt update
apt upgrade
apt-get install ansible
```
## Configuration
### Create the ansible user
Add a user for ansible (doesn't need to be called ansible, but that way everything is more easy to follow):
`sudo userad ansible`
The ansible doesn't necessarily need a password on the controll node. It is safer not to give it one because then it cannot ssh to the controll node.

Also, add this user on the managed nodes. There the ansible user needs a password for later logging in via ssh:
`sudo passwd ansible`

### Generate ssh key
As the ansible user on the controll node, generate an ssh key:
`ssh-keygen`
Public and private key will be stored in `/home/ansible/.ssh/`. Ensure that the directory exists and belongs to the ansible user.

The key can be copied to the managed node via `ssh-copy-id <managed-node-hostname>` for which the ansible user's password on the managed node is necessary.
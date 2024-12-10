# User Management

sudo su -

* when we create user in linux distro, by default it will create a group with the same name

/etc/passwd  --> it gives user info

/etc/group --> it gives group info

* id gives current logged in user

create user sekhar
```
useradd sekhar
```

set the password for the user sekhar

```
passwd sekhar
gpasswd sekhar
```
**gpasswd is used to manage group passwords and permissions.***

create a group devops and add the user sekhar to it.
create a group testing and add the user sekhar to it as secondary group

```
groupadd devops
usermod -g devops sekhar
groupadd testing
usermod -aG testing sekhar
```

remove the user from the group

```
gpasswd -d sekhar testing
```

```
gpasswd -d sekhar devops

[root@ip-172-31-88-195 ~]# gpasswd -d sekhar devops
Removing user sekhar from group devops
gpasswd: user 'sekhar' is not a member of 'devops'

[root@ip-172-31-88-195 ~]# id sekhar
uid=1001(sekhar) gid=1002(devops) groups=1002(devops)

```

***though console output shows sekhar is not a member of devops, `id sekhar` shows user still assigns to devops group. when we delete the user from the devops, system doesnt allow to delete it. user must be assigned to atleast one group. so, instead of removing the user from all the groups, user must be assigned to default group***

```
usermod -g sekhar sekhar
userdel sekhar
```

```
$ ssh sekhar@54.91.211.194
sekhar@54.91.211.194: Permission denied (publickey,gssapi-keyex,gssapi-with-mic).
```
after creation of user sekhar and password reset, login gets failed as user sekhar due to linux system expects key based authentication bydefault. we have to change the configuration and restart sshd service for password authentication.

```
vim /etc/ssh/sshd_config
PasswordAuthentication yes
```
* restart sshd service.
```
systemctl restart sshd
```

now it allows for password authentication


# key based authentication

Administrator will create authorized_keys file under /home/sekhar/.ssh folder and sekhar will provide the public generated using command `ssh-keygen -f <file-name>`. then admin will place the public key and give required permissions and ownership

```
.ssh> chmod 400 authorized_keys
/home/sekhar> chmod 500 .ssh
/home/sekhar> chown -R sekhar:sekhar .ssh
```


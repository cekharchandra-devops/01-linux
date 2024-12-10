# package management

A software have lot of dependencies on other softwares

yum --> dnf

early days, yum is used as package manager to download all the transitive dependencies.

now a days dnf is more popular.


* To install any package in linux, we can use either yum or 

```
cd /etc/yum.repos.d

[root@ip-172-31-88-195 yum.repos.d]# cat amazonlinux.repo
[amazonlinux]
name=Amazon Linux 2023 repository
mirrorlist=https://al2023-repos-$awsregion-de612dc2.s3$dualstack.$awsregion.$awsdomain/core/mirrors/$releasever/$basearch/$mirrorlist
priority=10
enabled=1
repo_gpgcheck=0
type=rpm
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-amazon-linux-2023



```

we can find all the repos under the folder mentioned.

each repo contains url gpgkey to download all the dependencies.

To install any software, list the softwares and remove we can use dnf

```
dnf install git 
```



```
dnf list installed
dnf list installed | wc -l
dnf list available
dnf remove git -y
```

how can check cpuinfo, memoryinfo

```
cat /proc/cpuinfo
cat /proc/meminfo
cat /etc/os-release
```

# Service Management

services start, restart, enable, stop, status, disable

```
systemctl start 
systemctl stop sshd
systemctl status sshd
systemctl enable sshd

```

To install Nginx and start the service

```
dnf install nginx
systemctl start nginx
systemctl enable nginx
systemctl status nginx

```
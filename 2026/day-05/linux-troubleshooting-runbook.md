# Day 05 – Linux Troubleshooting Drill: CPU, Memory, and Logs

## Task: Creating a runbook for linux system troubleshooting. 

### Environment basics

uname -a it shows the complete infromation about the system(ubuntu system)

ubuntu@ip-172-31-1-38:~$ uname -a 
Linux ip-172-31-1-38 6.14.0-1018-aws #18~24.04.1-Ubuntu SMP Mon Nov 24 19:46:27 UTC 2025 x86_64 x86_64 x86_64 GNU/Linux

cat /etc/os-release , it shows information about the operating system,

ubuntu@ip-172-31-1-38:~$ cat /etc/os-release 

PRETTY_NAME="Ubuntu 24.04.4 LTS"

NAME="Ubuntu"

VERSION_ID="24.04"

VERSION="24.04.4 LTS (Noble Numbat)"

VERSION_CODENAME=noble

ID=ubuntu

ID_LIKE=debian

HOME_URL="https://www.ubuntu.com/"

SUPPORT_URL="https://help.ubuntu.com/"

BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"

PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"

UBUNTU_CODENAME=noble

LOGO=ubuntu-logo


### Filesystem sanity

mkdir /tmp/runbook-demo , it will create a directory named runbook-demo under /tmp dir.

cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo , this command will copy all the content from /etc/hosts to /tmp/runbook-demo/hosts-copy and will list the content /tmp/runbook-demo
 
### CPU / Memory

for checking cpu consumption

top or htop , both command will show which process or service is using high cpu. by this command we can also get to know about memory usage by that process. 

free , or free -h (-h is for human readable form) , it will show how much memory is free in our system. 

# ubuntu@ip-172-31-1-38:~$ free -h 
               total        used        free      shared  buff/cache   available
               
Mem:           1.9Gi       412Mi       419Mi       2.7Mi       1.3Gi       1.5Gi

Swap:             0B          0B          0B


### Disk / IO  
df - h , it will show information about the disk, which partition is having how much space. 

du -csh  it will show how much spaces has been consumed. 

root@ip-172-31-1-38:/# du -csh 

2.9G	.

2.9G	total

### Network

ping , this command will ensure the connectivity between two host. 

netstat -tulpn  (t=tcp, u=udp,l=listening port, p=programming, n=numeric ports)

root@ip-172-31-1-38:~# netstat -tulpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      13810/nginx: master 
tcp        0      0 127.0.0.54:53           0.0.0.0:*               LISTEN      4864/systemd-resolv 
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1/systemd           
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      4864/systemd-resolv 
tcp6       0      0 :::80                   :::*                    LISTEN      13810/nginx: master 
tcp6       0      0 :::22                   :::*                    LISTEN      1/systemd           
udp        0      0 127.0.0.54:53           0.0.0.0:*                           4864/systemd-resolv 
udp        0      0 127.0.0.53:53           0.0.0.0:*                           4864/systemd-resolv 
udp        0      0 172.31.1.38:68          0.0.0.0:*                           4671/systemd-networ 
udp        0      0 127.0.0.1:323           0.0.0.0:*                           13450/chronyd       
udp6       0      0 ::1:323                 :::*                                13450/chronyd       

### Logs

journalctl -u <service> -n 50 , it is used to check realtime logs but if we are using -n 50 it will show only 50 lines.


tail -n 50 /var/log/nginx/error.log



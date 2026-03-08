# Day 07 – Linux File System Hierarchy & Scenario-Based Practice

## Part 1: Linux File System Hierarchy 

### Core Directories

/ (root) - This is the very first directory of the file system, it is like a reception of the hotel, we cannot enter any of the room without entering reception area, same we can not enter any of the directory under the / .

/home - This directory contains all the user accounts. 

/root - this is home directory of root(/) user

/etc - All the system configuration files are available here, for eg. /etc/hosts /etc/os-release /etc/group /etc/passwd 

/var/log - This directory contains all the system event logs,

/tmp - This holds program temporary files in it. on system reboot all the tmp file may removed from /tmp.

# Find the largest log file in /var/log

du -sh /var/log/* 2>/dev/null | sort -h | tail -5

ubuntu@ip-172-31-1-38:~$ du -sh /var/log/* 2>/dev/null | sort -h | tail -5

132K	/var/log/cloud-init.log

160K	/var/log/auth.log

404K	/var/log/syslog

596K	/var/log/sysstat

17M	/var/log/journal

# Part 2: Scenario-Based Practice
## Scenario 1: Service Not Starting

A web application service called 'myapp' failed to start after a server reboot.
What commands would you run to diagnose the issue?
Write at least 4 commands in order.

### systemctl status myapp

Why: by this command we can check the status of the service weather it is active or not.

### systemctl is-enabled myapp

Why: this command will tell us if the service is enabled on reboot.

### journalctl -u myapp -n 50 

why: this will used to watch the error logs 

### systemctl enabled myapp 

Why: if the service is not enabled, this command will ensure that service will get enabled on reboot.


## Scenario 2: High CPU Usage

Your manager reports that the application server is slow.
You SSH into the server. What commands would you run to identify
which process is using high CPU?

i can use top or htop for real time monitoring the cpu consumption by the process but we can filter by using 

ps -aux --sort=-%cpu |head -5  this will show first 5 top cpu consuming processes.

## Scenario 3: Finding Service Logs

A developer asks: "Where are the logs for the 'docker' service?"
The service is managed by systemd.
What commands would you use?



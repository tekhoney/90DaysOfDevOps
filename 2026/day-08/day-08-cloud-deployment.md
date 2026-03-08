# Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment

## Part 1: Launch Cloud Instance & SSH Access (15 minutes)
###        Step 1: Create a Cloud Instance : Done

###        Step 2: Connect via SSH :Done

/Downloads$ ssh -i ubuntu_practice.pem ubuntu@16.16.90.51
The authenticity of host '16.16.90.51 (16.16.90.51)' can't be established.
ED25519 key fingerprint is SHA256:MebsPMvITlfxNnaniPRXNXMfxNom8CqGATYZclVVylk.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:59: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? y
Please type 'yes', 'no' or the fingerprint: yes

   
## Part 2: Install Docker & Nginx (20 minutes)
###        Step 1: Update System : Done

###        Step 3: Install Nginx: Done

ubuntu@ip-172-31-1-38:~$ sudo apt install nginx
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
nginx is already the newest version (1.24.0-2ubuntu7.6).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


### Verify Nginx is running: Done

## Part 3: Security Group Configuration
Done

## Part 4: Extract Nginx Logs (15 minutes)
###        Step 1: View Nginx Logs

/var/log/nginx$ sudo journalctl -u nginx > nginx-logs.txt
-bash: nginx-logs.txt: Permission denied
ubuntu@ip-172-31-1-38:/var/log/nginx$ sudo journalctl -u nginx > /home/ubuntu/nginx-logs.txt
ubuntu@ip-172-31-1-38:/var/log/nginx$ cat /home/ubuntu/nginx-logs.txt 
Mar 07 05:27:42 ip-172-31-1-38 systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
Mar 07 05:27:42 ip-172-31-1-38 systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.
Mar 08 03:23:39 ip-172-31-1-38 systemd[1]: Stopping nginx.service - A high performance web server and a reverse proxy server...
Mar 08 03:23:39 ip-172-31-1-38 systemd[1]: nginx.service: Deactivated successfully.
Mar 08 03:23:39 ip-172-31-1-38 systemd[1]: Stopped nginx.service - A high performance web server and a reverse proxy server.
-- Boot d3cacb08784442e08e020c108f829980 --
Mar 08 07:49:21 ip-172-31-1-38 systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
Mar 08 07:49:22 ip-172-31-1-38 systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.
ubuntu@ip-172-31-1-38:/var/log/nginx$ ls 
access.log  error.log
ubuntu@ip-172-31-1-38:/var/log/nginx$ cat access.log 
123.57.94.251 - - [08/Mar/2026:08:09:26 +0000] "GET / HTTP/1.1" 200 409 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 14_7_4) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/18.3 Safari/605.1.15"
49.36.187.56 - - [08/Mar/2026:08:09:30 +0000] "GET / HTTP/1.1" 200 409 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/145.0.0.0 Safari/537.36"
49.36.187.56 - - [08/Mar/2026:08:09:31 +0000] "GET /favicon.ico HTTP/1.1" 404 196 "http://16.16.90.51/" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/145.0.0.0 Safari/537.36"
ubuntu@ip-172-31-1-38:/var/log/nginx$ cat access.log > /home/ubuntu/nginx-logs.txt 


###        Step 2: Save Logs to File

###        Step 3: Download Log File to Your Local Machine

opstree@opstree-Latitude-3420:~/Downloads$ scp -i ubuntu_practice.pem ubuntu@16.16.92.240:~/home/nginx-logs.txt .
^Copstree@opstree-Latitude-3420:~/Downloads$ scp -i ubuntu_practice.pem ubuntu@16.16.92.240:/home/nginx-logs.txt .
^Copstree@opstree-Latitude-3420:~/Downloads$ scp -i ubuntu_practice.pem ubuntu@16.16.90.51:/home/nginx-logs.txt .
scp: /home/nginx-logs.txt: No such file or directory
opstree@opstree-Latitude-3420:~/Downloads$ scp -i ubuntu_practice.pem ubuntu@16.16.90.51:~nginx-logs.txt .
scp: expand ~nginx-logs.txt: no such user
opstree@opstree-Latitude-3420:~/Downloads$ scp -i ubuntu_practice.pem ubuntu@16.16.90.51:~/home/ubuntu/nginx-logs.txt .
scp: ~/home/ubuntu/nginx-logs.txt: No such file or directory
opstree@opstree-Latitude-3420:~/Downloads$ ^C
opstree@opstree-Latitude-3420:~/Downloads$ scp -i ubuntu_practice.pem ubuntu@16.16.90.51:~/nginx-logs.txt .
nginx-logs.txt                                                                                 100%  582     1.4KB/s   00:00  


# Commands Used

cd /Downloads

chmod 400 ubuntu_practice.pen

ssh -i ubuntu_practice.pem ubuntu@16.16.90.51

sudo apt install nginx

sudo journalctl -u nginx > nginx-logs.txt

Challenges Faced
i faced issue with SCP command but i fixed it with R&D

What I Learned

#### I learnt launch an instance 
#### enabling the rules in ec2 (port 80)
#### usage of scp command.


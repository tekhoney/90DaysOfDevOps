# Day 11 – File Ownership Challenge (chown & chgrp)

## Create file devops-file.txt

touch devops-file.txt

## Check current owner:

ls -l devops-file.txt

## Change owner to tokyo (create user if needed)

ubuntu@ip-172-31-1-38:~$ sudo chown tokyo devops-file.txt 

ubuntu@ip-172-31-1-38:~$ ls -lrth devops-file.txt 

-rw-rw-r-- 1 tokyo ubuntu 0 Mar 10 16:47 devops-file.txt

## Change owner to berlin

@ip-172-31-1-38:~$ sudo chown berlin devops-file.txt 

## Verify the changes

ubuntu@ip-172-31-1-38:~$ ls -lrth devops-file.txt 

-rw-rw-r-- 1 berlin ubuntu 0 Mar 10 16:47 devops-file.txt

### Task 3: Basic chgrp Operations (15 minutes)

#### Create file team-notes.txt

touch team-notes.txt

#### Check current group: ls -l team-notes.txt

ubuntu@ip-172-31-1-38:~$ ls -l team-notes.txt 

-rw-rw-r-- 1 ubuntu ubuntu 0 Mar 10 16:53 team-notes.txt


#### Create group: sudo groupadd heist-team

ubuntu@ip-172-31-1-38:~$ sudo groupadd heist-team

#### Change file group to heist-team

ubuntu@ip-172-31-1-38:~$ sudo chgrp heist-team team-notes.txt 

#### Verify the change

ubuntu@ip-172-31-1-38:~$ ls -l team-notes.txt 

-rw-rw-r-- 1 ubuntu heist-team 0 Mar 10 16:53 team-notes.txt

## Task 4: Combined Owner & Group Change (15 minutes)

Create file project-config.yaml

touch project-config.yaml

Change owner to professor AND group to heist-team (one command)

ubuntu@ip-172-31-1-38:~$ sudo chown professor:heist-team project-config.yaml 

Create directory app-logs/

Change its owner to berlin and group to heist-team

# Task 5: Recursive Ownership (20 minutes)

## Create directory structure:

mkdir -p heist-project/vault

mkdir -p heist-project/plans

touch heist-project/vault/gold.txt

touch heist-project/plans/strategy.conf

### Create group planners: 

sudo groupadd planners

### Change ownership of entire heist-project/ directory:

Owner: professor

Group: planners

Use recursive flag (-R)


ubuntu@ip-172-31-1-38:~$ mkdir -p heist-project/vault

mkdir -p heist-project/plans

touch heist-project/vault/gold.txt

touch heist-project/plans/strategy.conf

ubuntu@ip-172-31-1-38:~$ sudo groupadd planners

ubuntu@ip-172-31-1-38:~$ sudo chown -R professor:planners heist-project/ 

ubuntu@ip-172-31-1-38:~$ ls -lR heist-project

heist-project:

total 8

drwxrwxr-x 2 professor planners 4096 Mar 10 17:00 plans

drwxrwxr-x 2 professor planners 4096 Mar 10 17:00 vault

heist-project/plans:

total 0

-rw-rw-r-- 1 professor planners 0 Mar 10 17:00 strategy.conf

heist-project/vault:

total 0

-rw-rw-r-- 1 professor planners 0 Mar 10 17:00 gold.txt


### Verify all files and subdirectories changed:

ls -lR heist-project/

files and subdirectories changed: ls -lR heist-project/

# Task 6: Practice Challenge (20 minutes)

## Create users: tokyo, berlin, nairobi (if not already created)

## Create groups: vault-team, tech-team

ubuntu@ip-172-31-1-38:~$ sudo groupadd vault-team

ubuntu@ip-172-31-1-38:~$ sudo groupadd tech-team

## Create directory: bank-heist/

ubuntu@ip-172-31-1-38:~$ mkdir bank-heist/

## Create 3 files inside:

ubuntu@ip-172-31-1-38:~$ touch bank-heist/access-codes.txt

touch bank-heist/blueprints.pdf

touch bank-heist/escape-plan.txt

### Set different ownership:

access-codes.txt → owner: tokyo, group: vault-team

blueprints.pdf → owner: berlin, group: tech-team

escape-plan.txt → owner: nairobi, group: vault-team

### Verify: ls -l bank-heist/


ubuntu@ip-172-31-1-38:~$ sudo chown tokyo:vault-team bank-heist/access-codes.txt 

ubuntu@ip-172-31-1-38:~$ cd bank-heist/

ubuntu@ip-172-31-1-38:~/bank-heist$ sudo chown berlin:tech-team blueprints.pdf 

ubuntu@ip-172-31-1-38:~/bank-heist$ sudo chown n escape-plan.txt 

news    nobody  

ubuntu@ip-172-31-1-38:~/bank-heist$ sudo chown nairobi:vault-team escape-plan.txt 

chown: invalid user: ‘nairobi:vault-team’

ubuntu@ip-172-31-1-38:~/bank-heist$ sudo useradd nairobi 

ubuntu@ip-172-31-1-38:~/bank-heist$ sudo chown nairobi:vault-team escape-plan.txt 

ubuntu@ip-172-31-1-38:~/bank-heist$ cd .. 

ubuntu@ip-172-31-1-38:~$ ls -l bank-heist/

total 0

-rw-rw-r-- 1 tokyo   vault-team 0 Mar 10 17:07 access-codes.txt

-rw-rw-r-- 1 berlin  tech-team  0 Mar 10 17:07 blueprints.pdf

-rw-rw-r-- 1 nairobi vault-team 0 Mar 10 17:07 escape-plan.txt

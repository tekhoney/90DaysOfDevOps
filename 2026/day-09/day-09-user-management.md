# Day 09 – Linux User & Group Management Challenge

## Users & Groups Created
- Users: tokyo, berlin, professor, nairobi
- Groups: developers, admins, project-team

## Group Assignments
tokyo is part of developer group

berlin is in developers and admins

professors is in admin

## Directories Created
mkdir /opt/dev-project


## Commands Used
useradd -m tokyo, berlin, professor, nairobi

usermod -aG tokyo  developers

usermod -aG berlin developers

usermod -aG berlin admins

usermod -aG professor admins

mkdir /opt/dev-project

chgrp developers dev-project

chmod 775 dev-project

usermod -aG nairobi project-team

usermod -aG tokyo project-team

mkdir /opt/team-workspace

chgrp project-team team-workspace

chmod 775 team-workspace



## What I Learned
i learnt how to manage Linux User & Group 

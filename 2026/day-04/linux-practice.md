Day 04 – Linux Practice: Processes and Services

Check running processes

we can check running processes by (ps, top, htop)

Inspect one systemd service

systemd services are the services which runs in the background, this is also called daemon, we can identify it by . (.ssh is daemon)

systemcctl is used to check services 

systemctl status nginx (To check the status of the service weather the service is active or inactive state)

systemctl start/restart/stop/enable/disable nginx (by this syntax we can start/restart/stop/enable/disable the service).


Capture a small troubleshooting flow

For troubleshooting.

we can check process by ps command
we can check service status of the service.
we can check logs journactl command or we can use tail command (tail -100 <file name>)



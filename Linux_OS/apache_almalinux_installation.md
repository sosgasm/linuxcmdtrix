# Quick and dirty dump on how to install Apache on Almalinux 

#### Prerequisites
##### Setup your Almalinux VM in Virtualbox first

```
https://almalinux.org  
visit website above for installation instructions. 
```
### The commands 

```
* $ ./autorun.sh  
* $ ./VBoxLinuxAdditions.run   
* $ sudo ./VBoxLinuxAdditions.run  
* $ sudo reboot  
* $ dnf install httpd  
* $ sudo dnf install httpd  
* $ systemctl enable httpd  
* $ systemctl start httpd  
* $ systemctl status httpd  
* $ firewall-cmd --zone=public --add-service=http --permanent  
* $ firewall-cmd --zone=public --add-service=https --permanent  
* $ firewall-cmd --reload  
```

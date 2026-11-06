# linux-administration-writeup
An ongoing writeup of my learning of RHEL 9 or Rocky Linux for system administration

## Lab 1: Hardened Apache Web Directory: <br>
**Goal** Configure a web server with a nonstandard web root ("/company_site") for apache httpd <br>
**Core Commands Used** <br>
chown -R apache:apache /company_site <br>
*Assigns a directory to be owned by apache* <br>
sudo chmod -R 750 /company_site <br>
*Restricts access to only apache* <br>
restorecon -Rv /company_site <br>
*Tells SELinux that apache is allowed to read files* <br>
**Notes:** <br>
<br>
<br>
## Lab 2: Changed port with SELinux and firewall security: <br>
**Goal** Change the port that our server listens on and modify SELinux and change firewall rules to accept it. <br>
**Core Commands Used** <br>
sudo nano /etc/httpd/conf/httpd.conf <br>
*Change the listening port from 80 to whatever you want to listen on, for this lab we will use 8080* <br>
**Notes** <br>
Make sure to restart apache with "sudo systemctl restart httpd" after changing the port



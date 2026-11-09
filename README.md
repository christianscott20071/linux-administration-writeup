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
## Lab 2: Changed port with SELinux: <br>
**Goal** Change the port that our server listens on and modify SELinux rules to accept it. <br>
**Core Commands Used** <br>
sudo nano /etc/httpd/conf/httpd.conf <br>
*Change the listening port from 80 to whatever you want to listen on, for this lab we will use 8070* <br>
sudo semanage port -a -t http_port_t -p tcp 8070 <br>
*Tells SELinux to add a port to the http_port_t label and specifies it as tcp and port 8070* <br>
**Notes** <br>
Make sure to restart apache with "sudo systemctl restart httpd" after changing the port <br>

## Lab 3: Modifying firewall access for a changed port <br>
**Goal** Our last lab established internal access with localhost curling the site, but we still need to make it so external clients can make it past the firewall and access this port. We need to let our firewall accept requests through port 8070 <br>
**Core Commands Used** <br>
sudo firewalld-cmd --permanent --add-port=8070/tcp <br>
sudo firewalld-cmd --reload <br>
sudo firewalld-cmd --list-ports <br>
*Confirms what ports are available* <br>



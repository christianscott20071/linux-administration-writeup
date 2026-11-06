# linux-administration-writeup
An ongoing writeup of my learning of RHEL 9 or Rocky Linux for system administration

## Lab 1: Hardened Apache Web Directory:
**Goal** Configure a web server with a nonstandard web root ("/company_site") for apache httpd
**Core Commands Used**
chown -R apache:apache /company_site
*Assigns a directory to be owned by apache*
sudo chmod -R 750 /company_site
*Restricts access to only apache*
restorecon -Rv /company_site
*Tells SELinux that apache is allowed to read files*


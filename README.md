# Using ngnix server on ec2 for hosting the portfolio on form of (http to https) request by self signed certificate.
## Bulid a nginx server in ec2 instance with http.
## Create a instance with Operating system (os) and name them.(choose the free tier version)
## Create a key pair save it on download.(go with the pem pair along RSA algorithm) as beginner.
## Allow  all the traffic from the HTTP(80),HTTPS(443),SSL(22).
## Connect with secure shell(ssh) link located on clicking the connect icon.
## Open the command prompt and chnage directory to Downloads. And then paste the copied ssh link.Then click on the enter button.It will ask for confrim, click yes.
## Now you are in remote server.
## Update ngnix
**sudo apt update**
## install nginx server to ec2
**sudo apt install nginx -y**
## once done, start server by 
**sudo systemctl start nginx**
## For enabling the server 
**sudo systemctl enable nginx**
## After this locate the resume pathe (Source config).
 **sudo rm -rf /var/www/html/*(or) /var/www/html/***
## Check for the index.html file and paste all source code into them and save it.
## view by cat command to verify whether they saved or not ?
## Then restart the server
**sudo systemctl restart nginx**
## Once all done navigate to the ec2 public ip on the new tab with http request on search bar.
## Finally host is done.(http request on server on on ec2 accomplished).
# Now we are going to create a self signed certificate for the secure of http as https.
## executes the following command.
**sudo openssl req -x509 -nodes -days 365 \
-newkey rsa:2048 \
-keyout /etc/ssl/private/selfsigned.key \
-out /etc/ssl/certs/selfsigned.crt**
## Using this command, Press enter for all entities.
## For https we need the domain name we don't have it then to overcome this we go for self signed key concept.
**ls -l /etc/ssl/private/selfsigned.key** *use sudo as root.
## once done you will see -----> "-rw------- 1 root root 1704 Dec 13 07:19 ".
**/etc/ssl/private/selfsigned.key**
**Command**
**ubuntu@ip-172-31-20-26:~$ sudo ls -l /etc/ssl/certs/selfsigned.crt**
## You notice that 
**-rw-r--r-- 1 root root 1245 Dec 13 07:20 /etc/ssl/certs/selfsigned.crt**
***sudo nginx -T**
## syntax and configuration are successfull and ok.Execute above command.
## once done you can redirect to public ip on ec2 instance on new tab working with the portfolio with not secure and striked https why because we are using self signed key instead of certificate of authority(ca) on secure socket layer(SSL).


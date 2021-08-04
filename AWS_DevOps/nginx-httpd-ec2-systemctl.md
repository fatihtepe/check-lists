- to see all running services
```
systemctl -a
```
- nginx and httpd do not work at same time and to stop one of the.

```
systemctl stop nginx
```
or
```
systemctl stop httpd
```
to activate
```
systemctl start httppd
```
port 80: nginx and httpd use same both if you run both of them at the same time. They will not run(crush)

```to remove nginx from your ec2```
```
sudo yum remove nginx
```
```
#!/bin/bash
yum update -y
amazon-linux-extras install nginx1.12
yum install -y wget
chkconfig nginx on
cd /usr/share/nginx/html
chmod o+w /usr/share/nginx/html
rm index.html
wget https://raw.githubusercontent.com/fatihtepe/fatihtepe.github.io/master/about.html
wget https://raw.githubusercontent.com/fatihtepe/fatihtepe.github.io/master/contact.html
wget https://raw.githubusercontent.com/fatihtepe/fatihtepe.github.io/master/index.html
wget https://raw.githubusercontent.com/fatihtepe/fatihtepe.github.io/master/profile.png
wget https://raw.githubusercontent.com/fatihtepe/fatihtepe.github.io/master/style1.css
service nginx start
```

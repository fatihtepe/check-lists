```
- chmod 400 testkey.pem
- ssh -i testkey.pem ec2-user@3.89.160.146
- sudo yum update -y
- sudo amazon-linux-extras install nginx1.12
- sudo yum install -y wget
- sudo systemctl start nginx
- sudo systemctl enable nginx
- cd /usr/share/nginx/html
- ls
 	404.html 50x.html index.html

- sudo rm index.html
- sudo wget https://raw.githubusercontent.com/....
- sudo systemctl restart nginx
```
---

```
#! /bin/bash

yum update -y
amazon-linux-extras install nginx1.12
systemctl start nginx
cd /usr/share/nginx/html
chmod -R 777 /usr/share/nginx/html
rm index.html
wget https://raw.githubusercontent.com/awsdevopsteam/ngniex/master/index.html
wget https://raw.githubusercontent.com/awsdevopsteam/ngniex/master/ryu.jpg
systemctl restart nginx
systemctl enable nginx
```

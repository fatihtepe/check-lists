```
- cd Downloads
- ls
	demo.pen
- chmod 400 demo.pen
- ls -l demo.pen
	-r--------@ 1 tepe  staff  1704 15 Jun 08:32 demo.pem
- ssh -i "demo.pem" ec2-user@ec2-34-207-125-204.compute-1.amazonaws.com
- sudo yum update -y
- sudo yum install httpd -y
- sudo systemctl status httpd
- sudo systemctl start httpd
- sudo systemctl status httpd
- sudo chmod -R 777 /var/www/html
- cd /var/www/html
- ls
- sudo wget https://raw.githubusercontent.com/fatihtepe/fatihtepe.github.io/master/contact.html
- sudo systemctl restart httpd
```

`Roles` `IAM` `EC2-S3`

```
#!/bin/bash
yum update -y
yum install -y httpd
chmod -R 777 /var/www/html
cd /var/www/html
aws s3 cp s3://osvaldo-pipeline-pro-2/index.html .
aws s3 cp s3://osvaldo-pipeline-pro-2/cat.jpg .
systemctl start httpd
systemctl enable httpd
```

# EC2-S3

```
#!/bin/bash
yum update -y
yum install -y httpd
chmod -R 777 /var/www/html
cd /var/www/html
aws s3 cp s3://catssss/static-web/cat0.jpg .
aws s3 cp s3://catssss/static-web/cat1.jpg .
aws s3 cp s3://catssss/static-web/cat2.jpg .
aws s3 cp s3://catssss/static-web/cat3.png .
aws s3 cp s3://catssss/static-web/index.html .
systemctl start httpd
systemctl enable httpd
```

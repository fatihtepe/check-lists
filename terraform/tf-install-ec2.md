```
sudo yum update -y
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
sudo yum -y install terraform
terraform version
```

https://learn.hashicorp.com/tutorials/terraform/install-cli?in=terraform/aws-get-started

`scp -i ~/.ssh/aws.pem README.md create_apache.sh tf-draw.png ec2-user@18.208.220.125:/home/ec2-user`

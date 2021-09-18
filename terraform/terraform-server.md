# to install terraform server

```
sudo yum update -y
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
sudo yum -y install terraform
sudo yum -y install git
sudo yum install tree -y
terraform --version
git --version
mkdir tf-files
cd tf-files
touch main.tf outputs.tf provider.tf sec-gr.tf user-data.sh
```

`or`

```
sudo yum update -y && sudo yum install -y yum-utils && sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo && sudo yum -y install terraform && sudo yum -y install git && sudo yum install tree -y && terraform --version && git --version && mkdir tf-files && cd tf-files && touch main.tf outputs.tf provider.tf sec-gr.tf user-data.sh
```
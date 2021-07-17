`install aws-cli to ubuntu` 

```
sudo apt-get update
sudo apt-get upgrade
aws --version
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo apt install unzip
unzip awscliv2.zip
sudo ./aws/install
aws --version
```

`install aws-cli to macOs`
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install awscli
```

`aws-cli configure`
```
AWS Access Key ID [None]:
AWS Secret Access Key [None]: 
Default region name [None]:
Default output format [None]:
```

`configures new_user profile`
```
aws configure --profile new-user 
```

`changes active user with new_user`
```
export AWS_PROFILE=new_user
```

if you have more than one user.. let's say you have default user and new_user .. you can easily change default user `export AWS_PROFILE=new_user` new_user. 
For example, if you want to reach s3 bucket you should write

`default user can list content of s3`
```
aws s3 ls 
```

`without changing default user you can check user_name's s3 bucket`
```
aws s3 ls user_name  
```

` to see who is active user`
```
aws sts get-caller-identity
```

`creates s3 bucket` 
```
aws s3 mb s3://benimbucketim
```

`copy file to bucket`
```
aws s3 cp test.txt s3://benimbucketim/ 
```

`delete bucket with force`
```
aws s3 rb s3://benimbucketim --force  # delete bucket
```

`will generate ec2 template`
```
aws ec2 run-instances --generate-cli-skeleton > demo.json 
```

`runs ec2 with json file`
```
aws ec2 run-instances --cli-input-json file://demo.json
```


`describes instance info`
```
aws ec2 describe-instances 
```

`stops ec2 with id number`
```
aws ec2 stop-instances --instance-ids i-001f367f22424af20
```


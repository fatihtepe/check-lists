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

```
aws configure --profile (new-user)==> adds a new user 
```
```
export AWS_PROFILE=(user) ==> changes default user
```

if you have more than one user.. let's say you have default user and dev user .. you can easily change default user `export AWS_PROFILE=dev` to dev user. 
For example, if you want to reach s3 bucket you should write

```
aws s3 ls (for default user)
```
or if you are not default use you should write like below: 

```
aws s3 ls dev ==> (without making dev user default user)
```

```
aws sts get-caller-identity ==> to see who is default user
```


```
aws ec2 describe-instances # describes instance info
```

creates s3 bucket 
```
aws s3 mb s3://benimbucketim
```

```
aws s3 cp test.txt s3://benimbucketim/ # copy file to bucket
```

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
`stops ec2 with id number`
```
aws ec2 stop-instances --instance-ids i-001f367f22424af20
```


[What is the AWS Command Line Interface?
](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)

The AWS Command Line Interface (AWS CLI) is an open source tool that enables you to interact with AWS services using commands in your command-line shell. With minimal configuration, the AWS CLI enables you to start running commands that implement functionality equivalent to that provided by the browser-based AWSManagement Console from the command prompt in your terminal program:

[Installing, updating, and uninstalling the AWS CLI version 2](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)

[How to Install and Configure the AWS CLI on a Mac](https://graspingtech.com/install-and-configure-aws-cli/)

[Installing, updating, and uninstalling the AWS CLI version 2 on Linux](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html)

[Named profiles](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html)

[AWS CLI Command Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/index.html)

[Command completion](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-completion.html)

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
- install homebrew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
- install awscli
```
brew install awscli
```

`aws configure`
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
aws s3 ls --profile user_name
```

`to see all users`
```
aws configure list-profiles
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

`list inside bucket`
```
aws s3 ls s3://benimbucketim
```
`remove file within bucket`
```
aws s3 rm s3://benimbucketim/ec2-json
```
`remove empty bucket`
```
aws s3 rm s3://benimbucketim
```

`delete bucket with force`
```
aws s3 rb s3://benimbucketim --force
```

`will generate ec2 template`
```
aws ec2 run-instances --generate-cli-skeleton > demo.json
```

`runs ec2 with json file`
```
aws ec2 run-instances --cli-input-json file://demo.json
```
`run an instance`
```
aws ec2 run-instances \
   --image-id ami-0dc2d3e4c0f9ebd18 \
   --count 1 \
   --instance-type t2.micro \
   --key-name [write key here without bracket]
```

`describes instance info`
```
aws ec2 describe-instances
```

`stops ec2 with id number`
```
aws ec2 stop-instances --instance-ids i-001f367f22424af20
```

`terminate ec2 instance`
```
aws ec2 terminate-instances --instance-ids i-0f8cbd611cc88a778
```
[InstanceState](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_InstanceState.html)
```
0 : pending

16 : running

32 : shutting-down

48 : terminated

64 : stopping

80 : stopped
```

`to list iam users`
```
aws iam list-users
```
`to create an iam user`
```
aws iam create-user --user-name [aws-cli-user]
```

`to delete an iam user`
```
aws iam delete-user --user-name [aws-cli-user]
```
`to see account aws account number`
```
aws sts get-caller-identity --query Account --output text
```
`Go to Amazon DynamoDB Load Data into Tables and download sampledata.zip file to the local with wget command.`

```
wget https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/samples/sampledata.zip
```

`Unzip sampledata.zip file into the dynamodb folder.There should be four unzipped files.`

```
unzip sampledata.zip
```

`Populate --> Insert data in to the tables`

`CRUD`(Create, Read or Retrieve, Update, Delete) Operatons

`Upload sample data into the DynamoDB tables; Populate the ProductCatalog table with data using AWS CLI.`

```
aws dynamodb batch-write-item --request-items file://ProductCatalog.json
```

`Populate the Forum table with data using AWS CLI.`

```
aws dynamodb batch-write-item --request-items file://Forum.json
```

## Use the `--dryrun` Flag in the AWS CLI Before Performing Any Task on Production Resources

Thanks to the --dryrun flag, the command-line output provides information about which files will be copied to S3. This command `only operates on CSV files` and doesn't move other files to S3:

```
aws s3 cp /path/to/local/files/ s3://demo-datasets/path/ --exclude "*" --include "*.csv" --dryrun
```

## Use --dryrun To Check if Two S3 buckets Are in Sync

By using the aws s3 sync command, you can check whether S3 buckets (or specific paths) are in sync: If there are any differences, the --dryrun flag will show them in the console without transferring anything.

```
aws s3 sync s3://bucket1 s3://bucket2 --dryrun
```
## Use --dryrun To Check if an S3 Bucket and a Local Folder Are in Sync

```
aws s3 sync /Users/.../path/ s3://mybucket --dryrun
```

## Quickly Download Many Files From S3

The last S3 command is `aws s3 cp`, which allows us to download all files from a specified S3 path:

```
aws s3 cp s3://mybucket /Users/.../path/ --recursive --storage-class STANDARD
```

In the same way, we can upload a bunch of files while specifying the S3 storage class that is most suitable to those objects:

```
aws s3 cp /Users/.../path/ s3://mybucket  --recursive --storage-class STANDARD
```


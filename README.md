
# Installing the CodeDeploy agent on EC2
```
#!/bin/bash
sudo yum update -y
sudo yum install -y ruby wget
wget https://aws-codedeploy-us-east-1.s3.us-east-1.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto
sudo service codedeploy-agent status
```
# Installation Commands
SSH into ec2 server
- $ nano script.sh = insert installation code
- $ chmod 755 script.sh
- $ ./script.sh

# Create EC2 with S3 access
Pushin Code to S3 is Optional unless you want to store your artifacts in S3

# create a bucket and enable versioning
- ensure u have configured cli on cmd prompt
```
aws s3 mb s3://aws-devops-edureka --region us-east-1 
aws s3api put-bucket-versioning --bucket aws-devops-edureka --versioning-configuration Status=Enabled --region us-east-1  
```

# deploy the files into S3
```
aws deploy push --application-name web-server --s3-location s3://aws-devops-edureka/codedeploy-demo/app.zip --ignore-hidden-files --region us-east-1 
```
# Configure CodePipeline
```
Configure CodePipeline to deploy on test servers and set a manual approval stage with an SNS notification to deploy on prod servers
```

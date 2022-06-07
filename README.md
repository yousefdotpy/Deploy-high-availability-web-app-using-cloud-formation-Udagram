
# Deploy a high availability web app using AWS CloudFormation

The 2nd project of Udacit Cloud DevOps Engineer nanodegree

# Problem scenario
Assuming a company is creating an Instagram clone called Udagram
Developers wanted to deploy a new application to the AWS infrastructure.\
My task was to create a high availability infrastructure and deploy it throug AWS using CloudFormation.


## Deployment

### To deploy the network stack run

```bash
$  aws cloudformation create-stack --stack-name network --template-body file://udagram-network.yml --parameters file://udagram-parameters.json --region=us-east-1
```
#### That will creat the following resources:
* VPC
* Internet Gateway
* Public subnets
* Private subnets
* Route tables
* Routes
* Nat Gateways
### To deploy the servers stack
```bash
$  aws cloudformation create-stack --stack-name servers --template-body file://udagram-servers.yml --parameters file://servers-parameters.json --region=us-east-1 --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM"
```
#### That will creat the following resources:
* IAM Role for S3 and its policy
* Load balancer
* Targer group
* Security groups
* Auto scaling group
* Launch configration
## Deleting the stacks
### To delete the stacks


```bash
$ aws cloudformation delete-stack --stack-name network
$ aws cloudformation delete-stack --stack-name servers
```

## To view the website 
Please click the link below

[Udagram](http://serve-webse-1trc2gm01d7m4-1482192828.us-east-1.elb.amazonaws.com/) `` Or`` http://serve-webse-1trc2gm01d7m4-1482192828.us-east-1.elb.amazonaws.com/

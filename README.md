# Cloud-Native Marketing Workload 

## Business Use Description 

A new company would like to run a marketing campaign to develop prospects. Digital ads will be run on various platforms to raise awareness of the service. These ads will drive traffic to a landing page. The company will rely on the landing page to collect information from the visitors, and this information will be stored and used for analysis to continually improve the marketing campaign. Name, email, phone number, and location are examples of the data to collect.

## Technical Description

### User Journey To Landing Page

The user will browse to https://www.resumematched.com. The landing page will be returned and the user will be asked to submit some information. After the data has been input, the user will hit submit and see a thank you message.

### Technical Journey of Landing Page

There is a CNAME record in Route 53 that points to the ELB. The user browses to https://www.resumematched.com. 

Using port 80, the Load Balancer sends the request to the EC2 Instances inside of the Auto Scaling Group located in private subnets. The EC2 Instances sends the landing page to the Load Balancer which serves it to the user. After the user submits their information, the data will go to an API Gateway. The data will go from the API Gateway to a DynamoDB table.

There are AWS Config rules in place to monitor the configuration of S3 Buckets, ELB & EC2 EBS Volumes.

There is a CloudTrail log to monitor amd record account activity.

Fuur S3 Buckets. One for each of the following: VPC Flow Logs, ALB Access Logs, New CloudFormation Templates & AWS Config recordings. The VPC Flow Logs, Cloudformation templates and AWS Config recordings buckets are all encrypted with AWS KMS keys. The ALB Access Logs bucket is encrypred with SSE:AES-256.


## Business Landing Page Link

Https://www.resumematched.com

## Template Order of Deployment

1. Governance Template
2. Networking Template
3. Compute Template
4. Application Template
5. Storage Template










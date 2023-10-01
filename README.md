# AWS-Projects
# AWS Project || VPC + EC2 Hands On 

To create networking on AWS which includes AWS VPC, Subnets, Internet Gateway, Route Tables, Security Groups along with a server inside the network.
Below diagarm shows the actual representation of our project.Follow those connections one by one.

![AWS Project](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/0d116c5f-fe47-4bf8-be5a-55cbc3731a6a)


**AWS Services**

Worked on Elastic Compute Cloud (EC2), Elastic Load Balancer (ELB), Auto Scaling, EBS Volumes, Virtual Private Cloud (VPC), Simple Storage Service (S3), Identity and Access Management (IAM), Route 53, Relational Database Service (RDS), Elastic File System (EFS), Simple Queue Service (SQS), Simple Notification Service (SNS), Simple Email Service (SES), Cloud Watch, Cloud Front, Cloud Formation, CloudTrail, Elastic Beanstalk, Trusted Advisor, Lambda and Terraform.

**Practical manner**

We have to follow 15 steps following below. Let's start

# Step 1 :

**a. VPC Creation:**

- Login to your AWS Acoount.

- Create the VPC.

- Give the name and it's ip address is must be (10.0.0.0/16).

- And remaining things are defalut just leave it.

- Click on create VPC.





**b. Subnets Creation:**

- In this project we need three subnets.Go to the subnet section and create.
- Fisrt take the subnets one by one.
- After that, attach existence VPC which we have create earlier.
- Give the names for every three subnets.
- Give availability zones for three subnets.
- And also give ipV4 CIDR blocks for each subnet as
- 1) 10.0.1.0/24
  2) 10.0.2.0/24
  3) 10.0.3.0/24
- Click on create subnet.
- Then out of three subnets we need to make two subnets as public.
- Let's do it, Click on subnet whicch we want to make subnets as public.
- Goto edit subnet and the "enable auto-assign public ipV4 address".
- Then click on save button.



**c. Internet Gateway(I.G)**

- Defaultly one I.G is there.
- But we need to craete another one.
- So,click on create I.G.
- Give the name whaterver you want then create.
- After this we need to attach this to existence VPC.


**d. Route Tables(R.T)**

- Defaultly one R.T is there.
- But, instead of default, there is another R.T is also there.Because, we are created one VPC.So,it is connected to it.
- Even though, we should create another R.T for our own.
- Give the name to new R.T and select existence  VPC  then click on create R.T .
- Now, our own R.T is ready.


- Follow the above diagram.
- Inside our R.T , goto edit subnet associations.Go through first two public subnets click on them.
- Another side, we should connect to I.G .Then gothrough the routes inside the R.T.   Edit routes manually we should do this.
- So, our target is I.G click on it.
- Moreover, we should provide internet right,then click on 0.0.0.0/0 for providing the internet.
- Save changes.


**e. NAT- Gateway(NAT.G)**

- I.G & NAT.G allows the internet.
- Create the NAT.G
- Goto the R.T, we know one R.T is there which is created when we are creating the VPC.
- Just go through and change the name as "NatRT".
- And see the picture and connection of NAT.G .



- Follow the above diagram.
- Now,inside the "NatRT". Go to the subnet permission click on third subnet and save.
- At the same, we should connect NAT.G  also, so, goto the route option inside the "NatRT". Click on NAT.G and provide internet.
- So, we are provided the internet to subnet-3 with the help of NAT.G and R.T .


# Step - 2:

**SNS(Simple Notification Services)**

- We have to create SNS.
- Go to the SNS create topic
- Create subscription click on E-mail.
- That's it.
- Goto E-mail and accept & Enable it.



# Step - 3:

**S3(Simple Storage Service)**

- Create S3 [3 Buckets]
- It is for VPC Flow Logs.
- Object ownership -Click on ACL's Enable and uncheck on block all public access and acknowledge.
- Create bucket.
- Create another two buckets named as
  1) First
  2) Second
- Process is same.




# Step - 4:

**IAM(Identified Access Management)**

- Goto role and click on create roles.Source is EC2 and next.
- Search S3 Full access and click it.
- Give the role name and click on next.
- Now IAM is ready.



# Step - 5:

**EFS(Elastic File System)**

- Create EFS and give the name click on existence VPC and click on create.
- There is a small Problem is there.
- So, we need to solve that problem.
- So,go through the VPC section we shpuld select our VPC and edit hostname option which is appear left corner.
- we have to enable it.
- Then only it can be work.
- That's it.



# Step - 6:

**Security Group(S.G)**

- Goto EC2 Section select the S.G.
- Create one new S.G.
- Give the name and attach our existence VPC.
- Goto edit outbound - first is all traffic. If anything is there just delete.
- Goto edit Inbound SSH to Myip & HTTP to all.
- Then click on craete.
- That's it.



# Step - 7:

**VPC Flow Log**

- Create VPC Flow Log [ It takes some time to enable,so that's why end of the creations.It will be ready]
- Go to the VPC . click on action and you can see create VPC Flow Log . Click it.
- Name it, send it to S3 bucket.
- Name S3 ARN bucket name.
- Then, goto the S3 .copy the ARN which you want to make it.
- Create Flow Log.

  # Step - 8:

  **Elastic Load Balancer(ELB)**

  - Create Clasic Load Balncer.
  - (If we have 0-100 servers then go with this).
  - Give any name and attach our VPC.
  - we want to connect our instances which is in public subnet. Then go through the first,second subnets-next.
  - Click on both default and our S.G.
  - (Why because, EFS is related to default one).
  - Health checks is same(2,5,2,2).
  - As of now we don't have any instances .Review & Create.
 


# Step - 9:

**Launch Template(L.T)**

- (Before going to the Autoscaling we need to craete the launch template.It is EC2)
- Give the name, Version(1),Provide guidlines.
- AMI, instances type(CPU,RAM)[Free tier].
- New Key Pair.
- Existence S.G [Both default, our S.G].
- EBS Volumes same[You can change 8 to 9].
- Advance,IAM role(Existence IAM role select).
- At teh end we need to install web packages
  #!/bin/bash
  sudo su -
  yum update -y
  mkdir /sai
  Goto EFS Select our EFS click on attach and copy and paste it here and write as /sai.
  yum install httpd -y
  echo "Mywebpage" > index.html
  service httpd start
  chkconfig httpd on
- Then create.


# Step - 10:

**AutoScaling**

- Click on AutoScaling.
- Give the name and select our launch template.
- next,click on our VPC and public subnet availability zone.
- next, Attach to existing load Balancer.
- Choose Classic Load Balancer,click on our Load Balnacer.
- Check on ELB and 150 seconds,next.
- Groupsize: desire(4),min(4),max(10).
- Target tracking click and target value(90),take a break 300 seconds,next
- SNS add it which we attached earlier when we are creating the launch template.
- next,Tags(Name-webserver).
- create AutoScaling.



- just copy any one of EC2 instance IP address and paste it on browser



- Goto the loadbalancer copy the DNS name & paste it in browser





**Note:**
As of now we created normal servers,which we have seen the results also .
But,further we can maove on to the bastion servers.And that is connected to third subnet.


# Step - 11:


**Bastion Server**

- Same goto EC2 section.
- Create instance and name it as bastion server.
- AMI, Instance types,select existing key pairs.
- Edit network & Security groups.
  1) Select our VPC.
  2) select first public subnet.Because, the bastion server launches in first public subnet.
  3) create new security group and name it.Because, we need to give the access for ourself.so,that's why select only SSH Port myself
- you can create another bastion server same as above.
- But, we need to select existing key pair,VPC,S.G and that too second bastion server.




# Step 12:


**DB Server**

- Same as EC2 Section.
- Create EC2 Instance name it as DBServer.
- AMI,Instance type,Select existing key pair.
- Edit network & Security groups.
  1) Select our VPC.
  2) Select third private subnet. Because, it is related to the third private subnet.
  3) Create new security Group & name it.
- DB
  1) Bastion server1(IP PRIVATE SSH PORT)
  2) Bastion server2(IP PRIVATE SSH PORT)
- MYSQL
  1) First Public Subnet(IP ADDRESS(10.0.1.0/24))
  2) Second Public Subnet(IP ADDRESS(10.0.2.0/24))




# Step 13:


**Route 53:**

-**Follow the below steps in route 53**

- Health Checks create, name it(NV-HC), take domain name.
- we need to North Verginia Load Balancer. DNS Name.
- Just copy it from L.B and paste it here
- path(index.html).
- Goto advance-Fast-Failure(1)-Next.
- Create alarm- Existing topic select & next.
- Now, goto hosted zones-create record.
- Click on Failover-next.
- Give the name- Define Failover record.
- Alias to application & Classic load balancer
- Select region.
- Select as primary,click on haelth check.
- Give the unique description & define it & Create record set.


# Step - 14:


**Cloudwatch**

- Goto Dashboard & create & nameit (AutoScaling Server).
- Select stacked area - metrics
- Scroll down goto EC2 - By AutoScaling Group.
- MYASG - CPU Utilization - Create widget.
- Save it.


# Step - 15:


**NACL[Network Access Control Lists]**

- Goto VPC.
- Click on NACL -Nmae it - Click our VPC -Create.
- This NACL is associate with two public subnets. click it in subnet associations.
- Then, you have to open the in & out bounds then only one servers will work.
- INBOUND RULES
  1) 100 - SSH(22)
  2) 200 - HTTP(80)
  3) 300 - Custom TCP
- OUTBOUND RULES
  1) 100 - SSH(22)
  2) 200 - HTTP(80)
  3) 300 - Custom TCP
  4) 400 - HTTPS - ALL(For access the internet in database)
 

# Testing all services

**1. Testing the Bastion Server**

- open the session.
- sudo su
- Drag .pem file & copy it here.
- Goto instance - SSH Client & Copy the Private IP - Yes.


**2. Testing the webservers**

-We did earlier, same process.


**3. IAM Role & S3 buckets Testing**

- Go to same webserver.
- sudo su -
- aws s3 ls


**4. Mount File**

- same webserver
- cd /
- ls
- sai(our file)
- cd sai
- touch sailfile
- ls
- mkdir saidir
- ls

**5. VPC Flow Logs**

- Goto S3 buckets- Inside objects -------.
- you can download it.

**6. Cloud Watch**

- You can see the CPU Optimization.

**7. Cloud Trail**

- Goto Cloud Trail - you can see everything so far- History.
  


# Conclusion

In this comprehensive AWS project, I successfully designed, implemented, and managed a scalable infrastructure utilizing a multitude of AWS services including EC2 instances, ELB for load balancing, Auto Scaling for dynamic resource management, EBS volumes, VPC for network isolation, S3 for object storage, IAM for access control, RDS for relational databases, and a range of other services such as CloudWatch, Lambda, and Terraform for efficient deployment and monitoring. By leveraging these tools, I created a robust and adaptable system that efficiently handled varying workloads while adhering to best practices in cloud architecture and management.




  








   



  





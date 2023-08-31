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

![1](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/99b90778-f0a7-44b5-8003-2aab5c418501)

![2](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/fe181509-f22e-45e5-9ad0-b5d03b3f4436)

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

![3](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/db24ccde-6fab-4c71-8540-4ec7edeb5b84)

![4](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/f6a7fadd-4d12-48e2-8afd-bb81db84e76e)

![5](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/46be75d7-35a0-4495-8f93-b55b5c9defe5)

![6](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/4fca6ebb-8ee9-454b-a22f-2c02651e9a61)

**c. Internet Gateway(I.G)**

- Defaultly one I.G is there.
- But we need to craete another one.
- So,click on create I.G.
- Give the name whaterver you want then create.
- After this we need to attach this to existence VPC.

![7](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/78f98fb2-6a18-4e06-a853-0c8653706512)
![8](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/a779c31d-585e-4c18-98bf-1b3287ecceda)

**d. Route Tables(R.T)**

- Defaultly one R.T is there.
- But, instead of default, there is another R.T is also there.Because, we are created one VPC.So,it is connected to it.
- Even though, we should create another R.T for our own.
- Give the name to new R.T and select existence  VPC  then click on create R.T .
- Now, our own R.T is ready.

![9](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/aa6351a0-9368-4163-a524-e448118cc0f6)

![1](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/7ad1c03b-dc82-423d-9a6b-0401ede69186)

- Follow the above diagram.
- Inside our R.T , goto edit subnet associations.Go through first two public subnets click on them.
- Another side, we should connect to I.G .Then gothrough the routes inside the R.T.   Edit routes manually we should do this.
- So, our target is I.G click on it.
- Moreover, we should provide internet right,then click on 0.0.0.0/0 for providing the internet.
- Save changes.

![10](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/687aa72d-7552-47e6-99be-cc0274ddbd55)

![11](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/24105d53-d00c-40e6-89ad-edd6d09e7e76)

**e. NAT- Gateway(NAT.G)**

- I.G & NAT.G allows the internet.
- Create the NAT.G
- Goto the R.T, we know one R.T is there which is created when we are creating the VPC.
- Just go through and change the name as "NatRT".
- And see the picture and connection of NAT.G .

![12](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/b896bb75-1cb3-410d-ad99-513856b73728)

![2](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/4b800a3d-e797-4c97-89df-9b65514e374b)

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

![13](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/2010b22e-5ba2-4191-8e16-1deabb2b6d2b)


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

![14](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/8f46fb39-255b-4f2b-8b05-435b1814c52a)


# Step - 4:

**IAM(Identified Access Management)**

- Goto role and click on create roles.Source is EC2 and next.
- Search S3 Full access and click it.
- Give the role name and click on next.
- Now IAM is ready.

![15](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/56aadadc-65bd-41fc-89fb-e195e56921c5)


# Step - 5:

**EFS(Elastic File System)**

- Create EFS and give the name click on existence VPC and click on create.
- There is a small Problem is there.
- So, we need to solve that problem.
- So,go through the VPC section we shpuld select our VPC and edit hostname option which is appear left corner.
- we have to enable it.
- Then only it can be work.
- That's it.

![16](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/a7a67234-6184-4773-afa0-4c164bdb65d6)

![17](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/5b3bd211-f3d6-4180-8105-31e03af7b096)


# Step - 6:

**Security Group(S.G)**

- Goto EC2 Section select the S.G.
- Create one new S.G.
- Give the name and attach our existence VPC.
- Goto edit outbound - first is all traffic. If anything is there just delete.
- Goto edit Inbound SSH to Myip & HTTP to all.
- Then click on craete.
- That's it.

![18](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/1cad6cc8-56a9-495e-acb9-e2965cc32b03)


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
 
![19](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/807cc807-7a15-4b61-b203-dc0487ac0b02)


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

![20](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/224dd430-e399-45bb-9609-91c73a072307)

![21](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/89cbbfff-6c8e-4297-96d5-b4af28f29fba)

- just copy any one of EC2 instance IP address and paste it on browser

![22](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/362b31d6-1573-4c56-be00-8df35507d138)

- Goto the loadbalancer copy the DNS name & paste it in browser

![23](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/8223b751-e810-4aad-aefb-705ca7d7646b)



**Note:**
As of now we created normal servers,which we have seen the results also .
But,further we can maove on to the bastion servers.And that is connected to third subnet.

  








   



  





# AWS-Projects
# AWS Project || VPC + EC2 Hands On 

To create networking on AWS which includes AWS VPC, Subnets, Internet Gateway, Route Tables, Security Groups along with a server inside the network.
Below diagarm shows the actual representation of our project.Follow those connections one by one.

![AWS Project](https://github.com/Harish-Sujanmulk-369/house-price-prediction/assets/100031745/0d116c5f-fe47-4bf8-be5a-55cbc3731a6a)


**AWS Services**

Worked on Elastic Compute Cloud (EC2), Elastic Load Balancer (ELB), Auto Scaling, EBS Volumes, Virtual Private Cloud (VPC), Simple Storage Service (S3), Identity and Access Management (IAM), Route 53, Relational Database Service (RDS), Elastic File System (EFS), Simple Queue Service (SQS), Simple Notification Service (SNS), Simple Email Service (SES), Cloud Watch, Cloud Front, Cloud Formation, CloudTrail, Elastic Beanstalk, Trusted Advisor, Lambda and Terraform.

**Practical manner**

We have to follow 15 steps following below. Let's start

**Step 1 :**

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



  





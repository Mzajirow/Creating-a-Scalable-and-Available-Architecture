![image](https://github.com/user-attachments/assets/850a15bb-22a5-46c6-a397-11ec22b0537e)![image](https://github.com/user-attachments/assets/f01581e8-fd2a-4942-a6dd-4176bc10b716)# Creating-a-Scalable-and-Available-Architecture

## 📝 Project Summary:
This project involved designing and deploying a scalable and highly available web application architecture on AWS. The café's website was migrated to a robust architecture that spans multiple Availability Zones, ensuring fault tolerance, load balancing, and auto scaling. Key AWS services used included VPC, EC2, Auto Scaling, Load Balancer, NAT Gateway, Launch Templates, and Security Groups.

## 🛠️ Tasks and Implementation (with Screenshots)
### Task 1: Inspecting the Environment
Description:
I reviewed the AWS environment to understand the existing VPC, subnets, and route tables before making changes.

VPC Overview 
![VPC Overview](https://github.com/Mzajirow/Creating-a-Scalable-and-Available-Architecture/blob/main/VPC%20existing%20setup%201.png?raw=true)

Resource map showing the subnets and route tables connection
![route table association](https://github.com/Mzajirow/Creating-a-Scalable-and-Available-Architecture/blob/main/VPC%20existing%20setup%202.png?raw=true)

### Task 2: Multi-AZ Network Update
✅ 2.1 Created a NAT Gateway for the second availablility zone.
Allocated Elastic IP and launched NAT Gateway in Public Subnet 2.

NAT Gateway Setup
![NAT Gateway](https://github.com/Mzajirow/Creating-a-Scalable-and-Available-Architecture/blob/main/NAT%20Gateway.png?raw=true)

✅ 2.2 Updated Route Table
Configured Private Subnet 2 to route outbound traffic through the new NAT Gateway.

Route Table Update
![Route Table Update](https://github.com/Mzajirow/Creating-a-Scalable-and-Available-Architecture/blob/main/NAT%20Gateway%20Configured.png?raw=true)

### Task 3: Launch Template Creation
In the process of creating a launch template, I configured the AMI, instance type, key pair, IAM role, tags, and security group.

Launch Template Configuration
![Launch Template](https://github.com/Mzajirow/Creating-a-Scalable-and-Available-Architecture/blob/main/Launch%20template%20setup.png?raw=true)

### Task 4: Auto Scaling Group Configuration
Created an Autoscaling group with desired capacity = 2, minimum capacity = 2, maximum capacity = 6. Also configured a target tracking policy for CPU utilization at 25%.

Auto Scaling Group Setup
Shows subnets selected and scaling policy details.
![ASG](https://github.com/Mzajirow/Creating-a-Scalable-and-Available-Architecture/blob/main/Auto%20Scaling%20Group%20Configured.png?raw=true)

Running Instances from ASG
Shows the two EC2 instances launched with the resource tag - webserver.
![ASG Instance](https://github.com/Mzajirow/Creating-a-Scalable-and-Available-Architecture/blob/main/New%20launched%20instances.png?raw=true)

🔹 Task 5: Load Balancer Setup
Created an Application Load Balancer (ALB) across Public Subnet 1 and 2. I also configured listener on port 80 and created a target group, which I assigned to the ALB. 

📸 Screenshot 5.1 – Load Balancer Configuration
Displays ALB settings and availability zones.

![ALB Settings](https://github.com/Mzajirow/Creating-a-Scalable-and-Available-Architecture/blob/main/Load%20Balancer%20Configured.png?raw=true)

Target Group & Health Check Setup
Shows health check path /cafe and status of registered targets.

![Target Group](https://github.com/Mzajirow/Creating-a-Scalable-and-Available-Architecture/blob/main/Target%20Group%20Configured.png?raw=true)


📸 Screenshot 5.3 – Load Balancer DNS in Browser
Verifies successful deployment by loading http://<ALB-DNS>/cafe.

🔹 Task 6: Testing & Validation
🧪 6.1 Initial Connectivity Test
Verified website is accessible through the ALB DNS and routing works.

📸 Screenshot 6.1 – Browser Test
Successful HTTP GET request to /cafe.

🔁 6.2 Auto Scaling Trigger Test
Used AWS Systems Manager to SSH into an instance.

Installed and ran stress to simulate high CPU usage.

📸 Screenshot 6.2 – SSM Session Terminal
Shows stress command running.

📸 Screenshot 6.3 – Auto Scaling Triggered
New instance(s) launched due to increased load.

📈 Outcome & Key Learnings
Implemented a highly available, secure, and auto-scalable architecture.

Learned how to manage networking with NAT Gateways and route tables.

Gained hands-on experience in SSM access, Launch Templates, and Load Balancer configuration.

Understood how Auto Scaling adapts to real-time demand spikes.

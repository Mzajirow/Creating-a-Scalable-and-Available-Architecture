# Creating-a-Scalable-and-Available-Architecture

## 📝 Project Summary:
This project involved designing and deploying a scalable and highly available web application architecture on AWS. The café's website was migrated to a robust architecture that spans multiple Availability Zones, ensuring fault tolerance, load balancing, and auto scaling. Key AWS services used included VPC, EC2, Auto Scaling, Load Balancer, NAT Gateway, Launch Templates, and Security Groups.

## 🛠️ Tasks and Implementation (with Screenshots)
🔹 Task 1: Inspecting the Environment
Description:
Reviewed the AWS environment to understand the existing VPC, subnets, and route tables before making changes.

📸 Screenshot Placeholder:
Screenshot 1.1 – VPC Overview
Shows existing VPC with 2 public and 2 private subnets.

📸 Screenshot 1.2 – Route Table Configurations
Highlights the default route table association and routes per subnet.

🔹 Task 2: Multi-AZ Network Update
✅ 2.1 Created a NAT Gateway for AZ2
Allocated Elastic IP and launched NAT Gateway in Public Subnet 2.

📸 Screenshot 2.1 – NAT Gateway Setup
Displays NAT Gateway in AZ2 with attached Elastic IP.

✅ 2.2 Updated Route Table
Configured Private Subnet 2 to route outbound traffic through the new NAT Gateway.

📸 Screenshot 2.2 – Route Table Update
Shows destination 0.0.0.0/0 route to new NAT Gateway.

🔹 Task 3: Launch Template Creation
Configured AMI, instance type, key pair, IAM role, tags, and security group.

📸 Screenshot 3.1 – Launch Template Configuration
Displays all settings: AMI ID, t2.micro instance type, key pair, IAM role, and user data (if applicable).

🔹 Task 4: Auto Scaling Group Configuration
Created an ASG with desired capacity = 2, min = 2, max = 6.

Configured a target tracking policy for CPU utilization at 25%.

📸 Screenshot 4.1 – Auto Scaling Group Setup
Shows subnets selected and scaling policy details.

📸 Screenshot 4.2 – Running Instances from ASG
Lists the two EC2 instances launched with tags webserver.

🔹 Task 5: Load Balancer Setup
Created an Application Load Balancer (ALB) across Public Subnet 1 and 2.

Configured listener on port 80 and registered target group.

📸 Screenshot 5.1 – Load Balancer Configuration
Displays ALB settings and availability zones.

📸 Screenshot 5.2 – Target Group & Health Check Setup
Shows health check path /cafe and status of registered targets.

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

# 🧑‍💼 Employee Directory App on AWS

A cloud-native **Employee Directory** application hosted on AWS that demonstrates two architectural approaches:
- 🖥️ Traditional architecture using **Amazon EC2**
- ⚡ Modern **Serverless** architecture using **AWS Lambda**

The app allows users to **add**, **view**, and **upload profile images** of employees. It's designed to be scalable, cost-effective, and secure — perfect for learning cloud architecture patterns.

---

## 📊 Architecture Diagrams

### 🖥️ EC2-Based Architecture

![EC2 Architecture](architecture-diagrams/ec2-architecture.png)

**Components**:
- **:aws: EC2** instance hosting a backend application
- **:aws: ALB** (Application Load Balancer) for routing traffic
- **:aws: VPC** with public/private subnets
- **:aws: S3** for image storage
- **:aws: DynamoDB** for employee records

---

### ⚡ Serverless Architecture

![Serverless Architecture](architecture-diagrams/serverless-architecture.png)

**Components**:
- **:aws: API Gateway** to expose RESTful endpoints
- **:aws: Lambda** functions for business logic and image resizing
- **:aws: DynamoDB** for employee data
- **:aws: S3** for static frontend and image uploads
- **:aws: CloudFront** for content delivery

---

## ✨ Key Features

| Feature | EC2 Architecture | Serverless Architecture |
|--------|------------------|--------------------------|
| Add/View Employees | ✅ | ✅ |
| Image Upload & Resize | ✅ via Lambda | ✅ via Lambda |
| Auto-scaling | Via ALB & ASG | Native to Lambda |
| Cost Efficiency | Less optimal | Highly optimized |

---

## 🔧 AWS Services Used

| Category | Services |
|---------|----------|
| **Compute** | :aws: EC2, :aws: Lambda |
| **Storage** | :aws: S3, :aws: DynamoDB |
| **Networking** | :aws: VPC, :aws: ALB, :aws: Route 53 |
| **Other** | :aws: IAM, :aws: CloudFront |

---

## 🚀 Setup Instructions

### ✅ Prerequisites

- AWS account with admin access
- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- Node.js and/or Python installed
- Terraform (optional for IaC)

---

### 🔨 Deployment Steps

Deploy EC2 Architecture (Manual or IaC)
Create the VPC, subnets, security groups.

Launch EC2 with IAM role and install backend.

Deploy frontend to S3.

Configure ALB and Route 53.

bash
Copy
Edit
cd terraform/ec2-architecture/
terraform init
terraform apply
4. Deploy Serverless Architecture
bash
Copy
Edit
cd terraform/serverless-architecture/
terraform init
terraform apply
OR use AWS SAM/CloudFormation templates in /backend/lambda

🛡 IAM Role Configuration
Refer to /policy-examples/ for least-privilege IAM policies.

EC2 Instance Profile with S3/DynamoDB access

Lambda Execution Role with:

S3:GetObject, PutObject

DynamoDB:PutItem, Scan

CloudWatch Logs permissions

📁 Code Structure
bash
Copy
Edit
/frontend           # Static HTML/CSS/JS for S3 hosting
/backend            # Node.js/Flask API for EC2 OR Lambda handlers
/terraform          # Infrastructure as Code (EC2 & Serverless)
/architecture-diagrams
/policy-examples
/sample-env-vars
.gitignore
LICENSE
README.md
🔐 Security Considerations
✅ IAM Roles follow least privilege principle

✅ Security groups restrict access by port and IP

✅ Data encrypted at rest (S3/DynamoDB) and in transit (HTTPS)

✅ S3 buckets are private with CloudFront public access

💰 Cost Optimization
Metric	EC2	Serverless
Idle Cost	High	Low
Scalability	Manual (ASG)	Auto
Maintenance	Manual patching	AWS-managed
Best For	Long-running apps	Event-driven logic

🧹 Cleanup Instructions
bash
Copy
Edit
cd terraform/ec2-architecture/
terraform destroy

cd terraform/serverless-architecture/
terraform destroy
Manually delete:

S3 buckets (after emptying)

DynamoDB tables

IAM roles

📚 Learning Resources
AWS EC2 Docs

AWS Lambda Docs

DynamoDB Docs

API Gateway Docs

Serverless on AWS (Coursera)

📄 License
Apache 2.0 – see LICENSE

🧽 .gitignore
Includes standard ignores for:

Node.js

Python

AWS SAM/.terraform

.env files

#### 1. Clone the Repository

```bash
git clone https://github.com/your-username/aws-employee-directory.git
cd aws-employee-directory

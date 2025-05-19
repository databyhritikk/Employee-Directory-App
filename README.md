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

#### 1. Clone the Repository

```bash
git clone https://github.com/your-username/aws-employee-directory.git
cd aws-employee-directory

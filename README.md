# AWS CloudFormation - VPC with Public Subnets and EC2 Instances

This project uses **AWS CloudFormation** to deploy a **VPC with two public subnets**, an **Internet Gateway**, and **two EC2 instances** running a simple web server. Each EC2 instance displays the **current date, time, and a greeting message** based on the time of day.

## 🚀 Features
- **VPC** with CIDR `10.0.0.0/16`
- **Two public subnets** (`10.0.1.0/24` & `10.0.2.0/24`)
- **Internet Gateway** for internet access
- **Public Route Table** with a default route (`0.0.0.0/0`)
- **Two EC2 instances** (one in each subnet) running Apache Web Server
- **User Data Script** to display:
  - Instance Name  
  - Current Date & Time  
  - Time-based Greeting (Good Morning, Afternoon, or Evening)

---

## 📌 Architecture Diagram

![Screenshot 2025-04-03 221826](https://github.com/user-attachments/assets/c5a0772e-f902-4c17-853b-56aaa2804efe)



---

## 📖 Deployment Instructions

### **1️⃣ Prerequisites**
- An **AWS account**
- A **Key Pair** in the **Mumbai region (`ap-south-1`)**
- **AWS CLI** installed (optional)

### **2️⃣ Deploy Using AWS CloudFormation**
#### **Method 1: AWS Console**
1. Go to **AWS CloudFormation** in the **Mumbai region (`ap-south-1`)**.
2. Click **Create Stack** → **With New Resources**.
3. Upload the `cloudformation-template.yaml` file.
4. Enter:
   - **Stack Name:** `Public-EC2-Mumbai`
   - **Key Pair:** Select an existing key pair.
5. Click **Next** → **Next** → **Create Stack**.
6. Wait for the deployment to complete (~5 minutes).

#### **Method 2: AWS CLI**
```sh
aws cloudformation create-stack --stack-name Public-EC2-Mumbai \
    --template-body file://cloudformation-template.yaml \
    --parameters ParameterKey=KeyName,ParameterValue=my-key-pair \
    --region ap-south-1

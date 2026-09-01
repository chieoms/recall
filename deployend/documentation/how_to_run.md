# How to Run

## Navigation

- **[Home](../../README.md)**
- **How to Run**
- **[Setup Script for Ubuntu](./scripts/ubuntu_setup.sh)**


---
Follow the steps below to deploy the project successfully.

## 1. Create an AWS Account

If you don't already have an AWS account, create one here:

- **AWS Account Registration:** https://signin.aws.amazon.com/signup?request_type=register

---

## 2. Purchase a Domain Name

Purchase a domain name from any domain registrar, such as:

- Amazon Route 53
- GoDaddy
- Namecheap
- Cloudflare Registrar
- Any other domain registrar

### If you use Amazon Route 53

Create a **Hosted Zone** for your domain.

### If you use another registrar (GoDaddy, Namecheap, etc.)

Update your domain's **nameservers** to the nameservers provided by your Route 53 Hosted Zone so that AWS can manage your DNS records.

> **Note:** This step is required for this project.

See the nameserver configuration walkthrough here:

- **Walkthrough:** *(will be added later)*

---

## 3. Install Required Tools

An installation script is provided for **Ubuntu 22.04+**.
[see script](./scripts/ubuntu.sh)

The script installs:
- Python 3
- Git
- Terraform
- AWS CLI v2
- Ansible

---

## 4. Configure AWS CLI

Create an **IAM User** with the required permissions and generate an **Access Key**.

Configure the AWS CLI:

```bash
aws configure
```

Enter the following when prompted:

- AWS Access Key ID
- AWS Secret Access Key
- Default AWS Region
- Default output format (optional)

---

## 5. Clone the Repository

```bash
git clone repository-url
cd repository-folder
```

---

## 6. Configure the Project

rename `example_recall_config.json` to `recall_config.json:

Update the configuration values to match your environment before deploying. It will generate ENV variables for the `frontend` and `backend` directory.

---

## 7. Deploy the Infrastructure

Run:

```bash
python3 main.py
```

This script will:

- Provision the AWS infrastructure
- Configure the EC2 instance (servers)
- Deploy the website

---

## 8. Destroy the Infrastructure

To remove all resources created by the project, run:

```bash
python3 destroy.py
```

---

## 9. View Logs

Deployment logs are available in the `deployend/logs/` directory.

Use these logs to monitor progress or troubleshoot issues.

---


# Notes

- Do **not** manually delete files or directories created by the application.
- Avoid deleting files listed in `.gitignore`, as they are automatically created and managed by the deployment scripts.
- Always use `python3 destroy.py` to remove AWS resources instead of deleting them manually from the AWS Console.

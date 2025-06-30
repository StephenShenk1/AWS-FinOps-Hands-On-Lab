# AWS FinOps Hands-On Lab Guide with Control Tower

Welcome to the **AWS FinOps Live Demo Lab** using Control Tower and Landing Zone!
This project helps you demonstrate real-world AWS cloud cost management and optimisation using built-in AWS tools.

---

## 📁 Project Structure

- **AWS Organization ID**: `o-xxus3ksxxu`
- **Main Accounts Used**:
  - `Sodaka DevOps` (Control)
  - `Sandbox_OU` (Workload simulation)
  - `Security_OU` (Billing, Audit)

---

## ✅ Objective

To simulate a production-like environment for **Cloud Cost Optimisation** and **FinOps best practices**, and demonstrate:
- Budget alerts
- Cost Explorer analysis
- Compute Optimizer savings
- Cost anomaly detection
- Consolidated billing

---

## 🛠️ Step-by-Step Setup

### 1. Enable FinOps Tools (In Management Account)
```bash
- AWS Cost Explorer
- AWS Budgets
- AWS Trusted Advisor
- AWS Compute Optimizer
```
✅ Ensure **consolidated billing** is enabled under AWS Organizations.

---

### 2. Simulate Real Usage (Sandbox_OU Account)
- Launch **EC2 Instances**: 2x t3.micro
- Deploy **RDS (Dev)**: t3.micro MySQL/Postgres
- Create **S3 Bucket** with lifecycle policy
- Deploy sample **Lambda function**

> Tag all resources:
```
Environment = Sandbox
Project = FinOpsLab
Owner = Sodaka
```

---

### 3. Set Up Cost Monitoring

- **Budgets**
```bash
Create actual cost budgets per OU
Set up usage-based thresholds (e.g., > 50 EC2 hours)
Enable email alerts
```

- **Cost Explorer**
```bash
Group by: Linked Account, Service, Tag
Filter by time range and usage type
```

- **Compute Optimizer**
```bash
Review right-sizing recommendations
Apply suggestions manually or track
```

- **Trusted Advisor**
```bash
Check for idle EC2s, EBS volumes, underutilized resources
```

---

### 4. Demo Health + Reporting

| Tool              | Purpose                      | Notes                            |
|------------------|------------------------------|----------------------------------|
| Budgets          | Alerts + Monthly thresholds  | Email team, slack/webhook ready |
| Compute Optimizer| Instance right-sizing        | Save 10–30%                      |
| Cost Explorer    | Visual billing insights      | Per team, tag, OU                |
| QuickSight       | Custom cost dashboard        | Optional for visualization       |
| Anomaly Detection| Spot unexpected costs         | Automatic alerts                 |

---

### 5. Automate + Enforce
- Use **SCPs** to:
  - Block launching expensive EC2 types (e.g. `m5.24xlarge`)
  - Deny untagged resource creation
  - Restrict creation in unapproved regions

---

## 🎯 Example CLI
```bash
aws ce get-cost-and-usage \
  --time-period Start=2025-06-01,End=2025-06-27 \
  --granularity MONTHLY \
  --metrics "UnblendedCost" \
  --group-by Type=TAG,Key=Project
```

---

## 🎓 What You'll Learn
- Set up a real FinOps lab across AWS accounts
- Track and reduce AWS cloud bills
- Create budgets, cost alerts, and anomaly detection
- Present cost-saving reports to teams or stakeholders

---

## 🔐 Security & Permissions
Use **IAM Identity Center** (SSO) to assign appropriate permission sets:
- `AWSReadOnlyAccess`
- `AWSPowerUserAccess`
- `BillingOnlyAccess`

---

## 💡 Bonus
- Export usage as **CSV Reports** or plug into QuickSight
- Use **Athena + CUR** for advanced analysis

---

## 📎 References
- [AWS Cost Explorer Docs](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html)
- [Compute Optimizer](https://docs.aws.amazon.com/compute-optimizer/latest/ug/what-is.html)
- [AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html)

---

## ✅ Final Note
This project gives you a **production-simulated lab** to build AWS FinOps skills using real services, structure, and billing behavior.

_“Optimize cost, maximize impact.”_

---
**Author**: [Sodaka DevOps](mailto:hello@sodaka.com)  

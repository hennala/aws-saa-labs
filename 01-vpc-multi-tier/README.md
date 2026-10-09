# Lab 01 — VPC Multi-Tier Architecture<Title>

## Business Problem
Build a 3-tier web app (public -> app -> DB) inside a VPC with public/private subnets across 2 AZs.

## Architecture
![Architecture](diagrams/arch.png)

## Prerequisites
- AWS account (Free Tier sufficient)
- Terraform ≥ 1.5, AWS CLI v2
- Region: `ap-south-2`

## Steps
1. Create VPC (10.0.0.0/16) with 2 public + 2 private subnets
2. Launch ALB in public subnets
3. Launch 2x EC2 (t3.micro) in private subnets, join ASG
4. Create RDS MySQL (db.t3.micro, Multi-AZ) in private subnets
5. Configure security groups (least privilege)
6. Verify failover by terminating an instance

## Results
| Test | Expected | Actual | Time |
|------|----------|--------|------|
| VPC Creation | VPC created with 2 public and 2 private subnet in <5 min | 3m 42s | ✅ |
| ALB Launch | ALB launched in <1 min | 47 s | ✅ |
| 2 EC2 instances | EC2 instances launched in private subnets <2 min | 1m 10s | ✅ |
| RDS MySQL Creation | db.t3.micro instances launched in private subnets <5 min | 2m 45s | ✅ |

## What I'd Do Differently at Enterprise Scale
> This is the section that differentiates a portfolio from a tutorial.

- **OCI comparison:** <E.g., "In OCI I'd use a Load Balancer + NSG + Security
  Lists; on AWS the equivalent is ALB + SG + NACL. The key trade-off is that
  OCI NSGs are stateful by default while AWS SGs are stateful but NACLs are
  stateless — so in production I'd rely solely on SGs and disable NACLs to
  avoid confusion.">
- **Scaling concern:** <E.g., "At 50+ nodes I'd move from a single ALB to
  multiple ALBs per AZ with Route 53 health-based routing.">
- **Compliance note:** <E.g., "For a regulated workload I'd add KMS CMK
  encryption on RDS and enable CloudTrail data events for the S3 bucket.">

## Cost
~$1.50/mo (Free Tier covers: 750 hrs t3.micro + 750 hrs db.t3.micro)

## Cleanup
```bash
cd terraform && terraform destroy
# or: ../cleanup.sh   

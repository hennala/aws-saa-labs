# Lab 01 — VPC Multi-Tier Architecture

## Scenario
Build a 3-tier web app (public → app → DB) inside a VPC with public/private subnets across 2 AZs.

## Architecture
![diagram](diagrams/arch.png)

## Steps
1. Create VPC (10.0.0.0/16) with 2 public + 2 private subnets
2. Launch ALB in public subnets
3. Launch 2× EC2 (t3.micro) in private subnets, join ASG
4. Create RDS MySQL (db.t3.micro, Multi-AZ) in private subnets
5. Configure security groups (least privilege)
6. Verify failover by terminating an instance

## Key Decisions
- Used NAT Gateway (not NAT Instance) for production-readiness
- ALB health check path: `/health`
- DB subnet group spans both AZs

## Cost
~$1.50/mo (Free Tier: 750 hrs t3.micro + 750 hrs db.t3.micro)

## Cleanup
```bash
cd terraform && terraform destroy   

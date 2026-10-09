# AWS SAA-C03 Hands-On Labs

**Sathish Bhat**

> Hands-on AWS labs built while preparing for SAA-C03, focused on secure, resilient cloud architecture.

## Labs

| # | Lab | Domain | Status |
|---|-----|--------|--------|
| 01 | [VPC Multi-Tier Architecture](01-vpc-multi-tier/) | Network & Design | 🚧 |
| 02 | [S3 + CloudFront Static Site](02-s3-cloudfront-static-site/) | Performance & CDN | 🚧 |
| 03 | [Auto Scaling + ALB](03-auto-scaling-alb/) | Resilience | 🚧 |
| 04 | [RDS Multi-AZ Failover](04-rds-multi-az-failover/) | Resilience & Data | 🚧 |
| 05 | [IAM Least Privilege](05-iam-least-privilege/) | **Security (30%)** | 🚧 |
| 06 | [Cost Optimization](06-cost-optimization/) | Cost (10%) | 🚧 |

## Conventions

- Each lab folder contains:
  - `README.md` — scenario, architecture, steps, enterprise-scale reflection
  - `diagrams/` — architecture diagram (PNG) + optional console screenshots
  - `terraform/` — IaC (`.tf` files, `variables.tf`, `outputs.tf`)
  - `cleanup.sh` — `terraform destroy` wrapper
- All resources tagged `Project=saa-labs` for cost tracking.
- Commit cadence: small, dated increments per lab (scaffold → build → verify → cleanup).

## Cost

All labs target the **AWS Free Tier** where possible. Estimated total: <$5/mo.

---

## About

Previously led a cloud-native service on **OCI**. These labs translate that
experience to AWS — each lab includes a short "enterprise-scale reflection"
comparing AWS choices to their OCI equivalents.   

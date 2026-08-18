# Tag Compliance Report

## Summary
- **Total Resources:** 
10 (S3 buckets: lojtiboy-tag-lab-01 through -10)

- **Tagged Resources:** 
10

- **Compliance Rate:** 
100%

## Non-Compliant Resources
None. All 10 buckets pass the AWS Config `required-tags` rule (Environment, Owner, Project, CostCenter all present).

## Remediation Plan
1. No remediation needed for current resources because all compliant.
2. Enable tag policies in AWS Organizations to enforce the same 4 required tags account-wide as real resources (EC2, RDS, etc.) are added.
3. Implement IaC tagging defaults (e.g. Terraform `default_tags` / CloudFormation stack-level tags) so new resources are tagged automatically at creation instead of relying on manual tagging after the fact.

## Screenshots
- costs-by-environment.png
- costs-by-owner.png
- config-compliance.png
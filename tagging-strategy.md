# Tagging Strategy

## Required Tags

1. **Environment:** 
production | staging | development

2. **Owner:** 
team name (e.g. lojtiboy, platform-team, data-team)

3. **Project:** 
project identifier (e.g. web-app, api-service, bootcamp, analytics)

4. **CostCenter:** 
department code (e.g. eng-001, eng-002, training, finance)

## Tag Naming Conventions

- Keys: PascalCase (`Environment`, `Owner`, `Project`, `CostCenter`)
- Values: lowercase-with-dashes (`web-application`, `api-service`)

## Enforcement

- AWS Config managed rule: `required-tags`, checking for Environment, Owner, Project, and CostCenter on all in-scope resources
- Applied manually via AWS CLI / Tag Editor for this lab; in production this would be enforced at resource creation via IaC templates (Terraform `default_tags`, CloudFormation stack tags) so nothing gets created untagged in the first place

## Lab Implementation Note

Since the account didn't have 10 existing taggable resources (EC2/RDS), 10 S3 buckets (`lojtiboy-tag-lab-01` through `-10`) were created specifically to satisfy the lab's minimum resource requirement. S3 buckets carry no cost, so this adds no billing risk. 
Tag values were varied across the 10 buckets (mixing production/staging/development, multiple owners, projects, and cost centers) to produce a meaningful split when viewed by tag in Cost Explorer.
- Applied at resource creation via IaC templates
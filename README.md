# Implementing Cost Allocation Tags

## Analysis Process

1. Designed a 4-tag taxonomy (Environment, Owner, Project, CostCenter) → documented in `tagging-strategy.md`.
2. Account had no existing 10+ taggable resources, so created 10 S3 buckets (`lojtiboy-tag-lab-01` to `-10`) via AWS CLI as free, zero-cost taggable resources.
3. Tagged all 10 buckets via CLI (`put-bucket-tagging`), varying values across Environment/Owner/Project/CostCenter for a meaningful split.
4. Verified tags landed correctly via `get-bucket-tagging` on each bucket.
5. Activated Environment, Owner, Project, CostCenter as cost allocation tags in Billing → Cost Allocation Tags.
6. Created an AWS Config `required-tags` rule scoped to check for all 4 tags → confirmed 100% compliance (10/10 buckets) once evaluation ran.
7. Documented compliance results in `tag-compliance-report.md`.
8. Pending: Cost Explorer views grouped by Tag (Environment, Owner). Cost allocation tags take up to 24h to propagate before they're selectable in Cost Explorer.

## Files

- `tagging-strategy.md` — tag taxonomy and naming conventions
- `tag-compliance-report.md` — compliance summary and remediation plan
- `config-compliance.png` — AWS Config compliance screenshot (10/10 compliant)
- `costs-by-environment.png` — pending, after 24h tag propagation
- `costs-by-owner.png` — pending, after 24h tag propagation
- `README.md` — this file
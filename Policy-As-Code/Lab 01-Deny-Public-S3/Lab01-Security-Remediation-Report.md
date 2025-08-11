# Lab 01: S3 Security Policy Remediation

## Security Vulnerability Identified
**Initial Configuration (VULNERABLE):**
```json
{
  "PublicAccessBlockConfiguration": {
    "BlockPublicAcls": false,  // DANGEROUS: Allows public access
    "IgnorePublicAcls": true,
    "BlockPublicPolicy": true,
    "RestrictPublicBuckets": true
  }
}
conftest test input.json --policy deny-public-s3.rego --all-namespaces
FAIL - input.json - s3 - S3 bucket allows public ACLs
{
  "PublicAccessBlockConfiguration": {
    "BlockPublicAcls": true,   // SECURE: Blocks public access
    "IgnorePublicAcls": true,
    "BlockPublicPolicy": true,
    "RestrictPublicBuckets": true
  }
}
conftest test input.json --policy deny-public-s3.rego --all-namespaces
1 test, 1 passed, 0 warnings, 0 failures, 0 exceptions

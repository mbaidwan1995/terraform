# AWS S3 with Terraform

A focused infrastructure-as-code lab that provisions one Amazon S3 bucket. This repository demonstrates a small, readable Terraform configuration and includes a GitHub Actions workflow.

## What is implemented

- AWS provider configured for `ap-south-1`.
- One `aws_s3_bucket` resource named `demo`.
- GitHub Actions configuration under `.github/workflows/`.

This is a learning example, not a complete production storage architecture.

## Repository layout

| Path | Purpose |
| --- | --- |
| `main.tf` | AWS provider and S3 bucket resource |
| `.github/workflows/` | Automation workflow configuration |

## Local validation

Prerequisites: Terraform and an AWS identity authorized for the resources you plan to manage. Configure authentication outside source control.

```bash
git clone https://github.com/mbaidwan1995/terraform.git
cd terraform
terraform fmt -check
terraform init
terraform validate
terraform plan
```

The bucket name in `main.tf` is a fixed example. Replace it with a globally unique name before planning a deployment. Review the plan before applying it. An AWS plan requires valid credentials; deployment creates billable resources.

## Troubleshooting

| Symptom | Check |
| --- | --- |
| Bucket name already exists | Choose a globally unique S3 bucket name |
| Access denied | Verify the active AWS identity and IAM permissions |
| Provider initialization fails | Check connectivity and Terraform provider installation |
| Unexpected changes in plan | Check the AWS account, region and local state before proceeding |

## Scope and next improvements

The current configuration does not explicitly define provider version constraints, a remote backend, public-access blocking, bucket versioning or encryption settings. These are useful next implementation steps; they are not claimed as existing features.

No deployment or live AWS verification is implied by this README. Keep credentials and Terraform state out of public commits. If you deploy the lab, use `terraform plan -destroy` to inspect cleanup before running `terraform destroy`; remove only resources you created for this exercise.

## Portfolio context

This example supports my interest in AWS cloud support, infrastructure troubleshooting and automation. See [my LinkedIn profile](https://www.linkedin.com/in/manjit-baidwan-a6a477406/) for professional experience.

# OpenTofu GCP Documentation

This repository contains documentation, notes, and learning material for using OpenTofu with Google Cloud Platform (GCP).

## Sections
- OpenTofu basics
- GCP provider setup
- Networking
- IAM configuration
- Cloud Run deployments
- Best practices

opentofu-gcp-docs/
│
├── 01-Introduction/
│     ├── what-is-opentofu.md
│     ├── why-use-opentofu.md
│     └── opentofu-vs-terraform.md
│
├── 02-Installation/
│     ├── install-opentofu.md
│     ├── install-gcloud-sdk.md
│     └── setup-vscode.md
│
├── 03-Provider-Setup/
│     ├── gcp-authentication.md
│     ├── provider-block.md
│     └── adc-vs-service-account.md
│
├── 04-GCP-Resources/
│     ├── compute.md
│     ├── storage.md
│     ├── cloudrun.md
│     ├── cloudsql.md
│     └── vpc.md
│
├── 05-Modules/
│     ├── what-are-modules.md
│     ├── module-structure.md
│     └── example-cloudrun-module.md
│
├── 06-IAM/
│     ├── service-accounts.md
│     ├── roles-and-permissions.md
│     └── workload-identity.md
│
├── 07-VPC/
│     ├── vpc-basics.md
│     ├── subnet-design.md
│     └── firewall-rules.md
│
├── 08-CloudRun/
│     ├── cloudrun-service.md
│     ├── cloudrun-lb-neg.md
│     └── cloudrun-ci-cd.md
│
├── 09-CloudSQL/
│     ├── cloudsql-basics.md
│     ├── private-ip-connection.md
│     └── sql-proxy-connector.md
│
└── 10-Best-Practices/
      ├── folder-structure.md
      ├── security-practices.md
      └── state-management.md

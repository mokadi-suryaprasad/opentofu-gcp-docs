# Multiple Local File Resources in OpenTofu

This document explains different ways to create multiple `local_file` resources in OpenTofu/Terraform.

---
```hcl
# Multiple resource blocks with the same name "example_resource"
terraform {
  required_providers {
    local = {
      source  = "hashicorp/local"
      version = "~> 2.1"
    }
  }
}
provider "google" {
  project = "project-fd1037d7-601e-4181-b3a"
  region  = "asia-south1"
}
resource "local_file" "learning_tofu" {
  filename        = "tofu.txt"
  content         = "I am learning OpenTofu"
  file_permission = "0770"
}
resource "local_file" "learning_gcp" {
  filename        = "gcp.txt"
  content         = "I am learning OpenTofu with GCP"
  file_permission = "0770"
}
```
---

## Method 1: Using `count`

```hcl
variable "files" {
  type    = list(string)
  default = ["file1.txt", "file2.txt", "file3.txt"]
}

resource "local_file" "multiple" {
  count             = length(var.files)
  filename          = var.files[count.index]
  sensitive_content = "Master OpenTofu with GCP"
  file_permission   = "0770"
}
```

---

## Method 2: Using `for_each` (Recommended)

```hcl
variable "file_map" {
  type = map(string)
  default = {
    "alpha.txt" = "Alpha content"
    "beta.txt"  = "Beta content"
    "gamma.txt" = "Gamma content"
  }
}

resource "local_file" "multi" {
  for_each          = var.file_map
  filename          = each.key
  sensitive_content = each.value
  file_permission   = "0770"
}
```

---

## Method 3: Using List of Objects

```hcl
variable "file_objects" {
  type = list(object({
    name    = string
    content = string
  }))

  default = [
    { name = "dev.txt",   content = "Development" },
    { name = "stage.txt", content = "Staging" },
    { name = "prod.txt",  content = "Production" }
  ]
}

resource "local_file" "obj_files" {
  for_each          = { for f in var.file_objects : f.name => f }
  filename          = each.value.name
  sensitive_content = each.value.content
  file_permission   = "0770"
}
```

---

## Summary

- Use `count` for simple filename lists
- Use `for_each` for unique content per file
- Use object lists for structured data


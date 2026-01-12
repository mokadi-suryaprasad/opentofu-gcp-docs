# OpenTofu -- Standard Input Variables Block

This document shows the recommended structure and syntax for defining
input variables in **OpenTofu** modules (`variables.tf`).

## 1. Basic Variable Structure

``` hcl
variable "name" {
  description = "Description of the variable"
  type        = string
}
```

## 2. String Variable

``` hcl
variable "project_id" {
  description = "GCP project ID"
  type        = string
}
```

## 3. Number Variable

``` hcl
variable "instance_count" {
  description = "Number of instances to create"
  type        = number
  default     = 1
}
```

## 4. Boolean Variable

``` hcl
variable "enable_feature" {
  description = "Enable or disable the feature"
  type        = bool
  default     = true
}
```

## 5. List Variable

``` hcl
variable "regions" {
  description = "List of GCP regions"
  type        = list(string)
}
```

## 6. Map Variable

``` hcl
variable "labels" {
  description = "Labels applied to resources"
  type        = map(string)
  default     = {}
}
```

## 7. Any Type Variable

``` hcl
variable "config" {
  description = "Configuration object (any type)"
  type        = any
}
```

## 8. Object Variable

``` hcl
variable "cloud_run_config" {
  description = "Cloud Run configuration settings"
  type = object({
    cpu       = number
    memory    = string
    min_scale = number
    max_scale = number
  })
}
```

## 9. Variable Validation

``` hcl
variable "environment" {
  description = "Deployment environment"
  type        = string

  validation {
    condition     = contains(["dev", "qa", "prod"], var.environment)
    error_message = "Environment must be one of: dev, qa, prod."
  }
}
```

## 10. Sensitive Variable

``` hcl
variable "db_password" {
  description = "Database password"
  type        = string
  sensitive   = true
}
```

## 11. Default Values

``` hcl
variable "region" {
  description = "GCP deployment region"
  type        = string
  default     = "asia-south1"
}
```

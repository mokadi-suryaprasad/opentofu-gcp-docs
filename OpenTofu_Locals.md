# OpenTofu Local Variables (locals)

`locals` in OpenTofu (Terraform OSS) allow you to define internal reusable values.

## Why locals?
- Avoid repetition
- Build environment-based names
- Keep code clean

## Syntax
```hcl
locals {
  env     = "dev"
  project = "suryacloud"
  name    = "${local.project}-${local.env}"
}
```

Use:
```hcl
local.name
```

## Example
```hcl
variable "env" {}

locals {
  project = "myapp"
  bucket  = "${local.project}-${var.env}-bucket"
}
```

## Best Practice
Use variables for inputs, locals for derived values.

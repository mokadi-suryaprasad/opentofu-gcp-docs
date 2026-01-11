# Local File Resource (`local_file`)

This example demonstrates how to use the `local_file` resource in OpenTofu to create files on your local machine.  
This is helpful for generating configuration files, templates, scripts, or storing sensitive output.

---

## Example

```hcl
resource "local_file" "example_resource" {
  filename          = "example.txt"
  sensitive_content = "Master OpenTofu with GCP"
  file_permission   = "0770"
}
```

---

## Field Explanation

| Field | Description |
|------|-------------|
| `filename` | Name or path where the file will be created |
| `sensitive_content` | Content written to the file; hidden from logs |
| `file_permission` | File permissions in Linux format (e.g., 0770) |

---

## Result

After running:

```
tofu apply
```

You will get a file:

```
example.txt
```

With content:

```
Master OpenTofu with GCP
```

And permissions:

```
-rwxrwx---
```

---

## When to Use This Resource

- Creating configuration files
- Writing output values to files
- Template generation during provisioning
- Storing sensitive data securely
- Local automation tasks

---

## Commands to Test

Initialize:

```
tofu init
```

Validate configuration:

```
tofu validate
```

Apply changes:

```
tofu apply
```


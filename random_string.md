# random_string Resource in OpenTofu

The `random_string` resource is used to generate a random string containing letters, numbers, or special characters.  
It is useful for creating passwords, unique names, secrets, IDs, and tokens.

---

## Example Usage

```hcl
resource "random_string" "example" {
  length  = 12
  special = false
  upper   = true
  lower   = true
  numeric = true
}

output "random_value" {
  value = random_string.example.result
}
```

---

## Field Explanation

| Field | Description |
|-------|-------------|
| `length` | Number of characters in the string |
| `special` | Include special characters (`!@#$%`) |
| `upper` | Include uppercase letters |
| `lower` | Include lowercase letters |
| `numeric` | Include digits |

---

## Example Output

```
random_value = "Ab7kP2xQmB9d"
```

Every `tofu apply` will generate a new string.

---

## Common Use Cases

- Password generation  
- Unique resource identifiers  
- Random suffix for bucket names  
- API keys and tokens  
- Temporary secrets  

---

## Commands to Test

```
tofu init
tofu plan
tofu apply
```

---


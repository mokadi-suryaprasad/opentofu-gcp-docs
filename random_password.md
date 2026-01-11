# random_password Resource in OpenTofu

The `random_password` resource is used to generate secure passwords with customizable length and character rules.  
It is commonly used for database passwords, service account secrets, and application credentials.

---

## Example Usage

```hcl
resource "random_password" "example" {
  length           = 16
  special          = true
  override_special = "!@#$%"
}

output "password" {
  value     = random_password.example.result
  sensitive = true
}
```

---

## Field Explanation

| Field | Description |
|-------|-------------|
| `length` | Total number of characters in the password |
| `special` | Include special characters |
| `override_special` | Customize which special characters are allowed |
| `upper` | Include uppercase letters (default: true) |
| `lower` | Include lowercase letters (default: true) |
| `numeric` | Include digits (default: true) |

---

## Example Output (hidden)

Because the output is marked *sensitive*, OpenTofu hides the value:

```
password = (sensitive value)
```

---

## Common Use Cases

- Database passwords (Cloud SQL, RDS, MySQL)
- Service account secrets
- API keys
- Admin passwords
- Random secure tokens

---

## Commands to Test

```
tofu init
tofu plan
tofu apply
```

---


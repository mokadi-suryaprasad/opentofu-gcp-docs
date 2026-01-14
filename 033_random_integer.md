# random_integer Resource in OpenTofu

The `random_integer` resource is used to generate a random whole number between a minimum and maximum value.  
This is useful for creating unique resource names, testing, and avoiding naming conflicts.

---

## Example Usage

```hcl
# Specify required providers and their versions
terraform {
  required_providers {
    google = {
      source  = "hashicorp/google"
      version = "~> 5.0"
    }
    random = {
      source  = "hashicorp/random"
      version = "~> 3.0"
    }
  }
}

resource "random_integer" "random" {
  min = 10
  max = 100
}

output "random_number" {
  value = random_integer.random.result
}

```

---

## Explanation

### `resource "random_integer" "random"`
Creates a random number resource.

### `min = 10`
The smallest allowed value.

### `max = 100`
The largest allowed value.

### Output
The output block prints the generated random number after `tofu apply`.

---

## Example Output

```
random_number = 47
```

Each apply may generate a different number.

---

## Why Use random_integer?

- Generate unique names  
- Avoid naming collisions  
- Useful for testing  
- Helps in dynamic resource creation

---

## Commands to Test

```
tofu init
tofu plan
tofu apply
```

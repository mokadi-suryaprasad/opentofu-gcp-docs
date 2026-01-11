# random_shuffle Resource in OpenTofu

The `random_shuffle` resource is used to generate a random ordering of a given list.  
It is useful when you need random selection, randomized ordering, or load distribution.

---

## Example Usage

```hcl
resource "random_shuffle" "example" {
  input        = ["red", "blue", "green", "yellow"]
  result_count = 4
}

output "shuffled_list" {
  value = random_shuffle.example.result
}
```

---

## Field Explanation

| Field | Description |
|-------|-------------|
| `input` | The list of values to be shuffled |
| `result_count` | Number of items to return from the shuffled list |

---

## Example Output

```
shuffled_list = [
  "green",
  "red",
  "yellow",
  "blue",
]
```

Each apply may produce a different order.

---

## Common Use Cases

- Random ordering of nodes
- Random item selection
- Load balancing test scenarios
- Simulating random behavior in environments

---

## Commands to Test

```
tofu init
tofu plan
tofu apply
```

---

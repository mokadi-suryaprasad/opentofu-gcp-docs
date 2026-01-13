# OpenTofu – Implicit and Explicit Dependencies

## What is a Dependency?
A dependency defines the order in which resources are created.

OpenTofu builds a dependency graph instead of executing line by line.

---

## Implicit Dependency
Created automatically when one resource references another.

### Example
```hcl
resource "google_storage_bucket" "site" {
  name = "my-site"
}

resource "google_compute_backend_bucket" "backend" {
  bucket_name = google_storage_bucket.site.name
}
```

OpenTofu understands that backend depends on site.

---

## Explicit Dependency
Used when OpenTofu cannot detect the relationship.

Defined using `depends_on`.

### Example
```hcl
resource "google_storage_bucket_iam_binding" "public" {
  bucket = google_storage_bucket.site.name
  role   = "roles/storage.objectViewer"
  members = ["allUsers"]
}

resource "google_compute_backend_bucket" "backend" {
  bucket_name = google_storage_bucket.site.name

  depends_on = [
    google_storage_bucket_iam_binding.public
  ]
}
```

This ensures the bucket is public before the backend is created.

---

## Module-Level Dependency
```hcl
module "lb" {
  source = "./modules/loadbalancer"
  bucket_name = module.gcs.bucket_name

  depends_on = [module.gcs]
}
```

---

## Best Practice
Use implicit dependencies wherever possible.  
Use explicit dependencies only when side effects (like IAM) exist.


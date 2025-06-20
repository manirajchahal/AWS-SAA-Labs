# IAM + S3 Lab – Real-World Use Case

This lab demonstrates how to use IAM policies to apply **fine-grained permissions** within a single S3 bucket.

---

## 🧠 Use Case

Imagine a situation where multiple teams or applications use the same S3 bucket, but need **different access levels** to different folders.

Instead of creating separate buckets for each user or group, we use **S3  folder paths** + **IAM policies** to control access.

---

## 🔄 Steps To Take

- Test this policy by creating a new `upload-user`
- Attach the `upload-only` policy (see [iam-policy/upload-only.json](./iam-policy/upload-only.json))
- Upload to `/upload/` – allowed ✅
- Upload to `/` or other folders – denied ❌

---

## 🧪 Example Scenario

| User/Team       | Allowed Folder                  | Permissions         |
|-----------------|----------------------------------|---------------------|
| `upload-user`   | `s3://maniraj-iam-test-bucket/upload/` | Upload only |
| `readonly-user` | `s3://maniraj-iam-test-bucket/`        | View only |
| `admin-user`    | `s3://maniraj-iam-test-bucket/*`        | Full access |

---

## 🔐 Why This Matters

- Supports **multi-tenant** architecture in a single bucket
- Enforces **least privilege** access
- Keeps your cloud infrastructure **simple and secure**
- Avoids cost and complexity of managing multiple S3 buckets



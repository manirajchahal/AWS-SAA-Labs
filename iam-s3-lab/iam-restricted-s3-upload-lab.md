# IAM Restricted S3 Upload Lab

This lab demonstrates how to restrict an IAM user (`upload-user`) to:
- Only view and upload to the `/upload/` folder of an S3 bucket
- Be denied access to everything else

---

## 📦 S3 Bucket Setup
- Bucket: `maniraj-iam-test-bucket`
- Folder created: `/upload/`
- Test file uploaded: `upload-user_upload.txt`

---

## 🔐 IAM Policy Applied

Policy allows:
- List all buckets (to use console)
- List inside `/upload/` only
- Upload to `/upload/`
- Read files from `/upload/`

Path: [`iam-policy/upload-only.json`](./iam-policy/upload-only.json)

---

## ✅ Expected Behavior

| Action                         | Expected Outcome |
|-------------------------------|------------------|
| See bucket name               | ✅ Yes           |
| List `/upload/`               | ✅ Yes           |
| Upload to `/upload/`          | ✅ Yes           |
| View `/upload/` file contents | ✅ Yes           |
| List bucket root              | ❌ No            |
| Upload outside `/upload/`     | ❌ No            |

---

## 🧠 Key Concepts

- `s3:ListAllMyBuckets` is required for console UI
- `s3:ListBucket` needs precise `s3:prefix` values (`""`, `"upload/"`, `"upload/*"`)
- S3 "folders" are simulated via object prefixes
- You don’t need multiple buckets for permission segmentation

---

## 🔄 Next Steps
- Create a `readonly-user` for `/upload/` only
- Try bucket policy instead of IAM policy
- Automate this with CloudFormation or Terraform

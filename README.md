# S3 Bucket File Migration Documentation

## Project Overview

This project is designed to facilitate a seamless migration of files from one AWS S3 bucket to another. The policy used here allows specific actions for listing, copying, and deleting files across two S3 buckets, enabling efficient and secure data transfer.

## Requirements

- AWS account with access to IAM (Identity and Access Management) and S3.
- AWS CLI or SDK (e.g., `boto3` for Python) configured with appropriate credentials.

## Policy Setup

To enable the migration, create an IAM policy with the following JSON code, assigning it to a role or user with the required S3 permissions..

## Step-by-Step Instructions

### Step 1: Configure AWS CLI
Ensure that AWS CLI is configured with a user that has the necessary permissions.
```bash
aws configure
```

### Step 2: List Files in Source Bucket (`retr0`)
Use the following command to list all files in the source bucket:
```bash
aws s3 ls s3://retr0 --recursive
```

### Step 3: Copy Files from Source to Destination (`v1ntage`)
Run the following command to copy all files:
```bash
aws s3 sync s3://retr0 s3://v1ntage
```

### Step 4: Verify the Migration
Check that files were copied successfully by listing the contents of the destination bucket:
```bash
aws s3 ls s3://v1ntage --recursive
```

### Step 5: Clean Up (Optional)
If you want to delete the migrated files from the source bucket, run:
```bash
aws s3 rm s3://retr0 --recursive
```

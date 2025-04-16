---
icon: bucket
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Amazon S3 Storage

The Amazon S3 Storage credential type stores the AWS credentials associated with an Amazon S3 bucket.

{% include "../../../.gitbook/includes/intermediate-storage-hint.md" %}

To configure an Amazon S3 Storage credential, you will need to provide:

* The S3 bucket name,&#x20;
* An AWS Access Key,&#x20;
* An AWS Secret Key, and
* The Bucket's AWS Region.



Your AWS Access and Secret keys should have the following permissions:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:GetObject",
                "s3:ListBucketMultipartUploads",
                "s3:AbortMultipartUpload",
                "s3:ListBucket",
                "s3:DeleteObject",
                "s3:ListMultipartUploadParts"
            ],
            "Resource": [
                "arn:aws:s3:::your-bucket-name",
                "arn:aws:s3:::your-bucket-name/*"
            ]
        }
    ]
}
```

\
For more information about creating an S3 bucket, refer to the [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/create-bucket-overview.html).

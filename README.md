#
# AWS Simple Storage Service (S3)

This guide provides a clear and practical introduction to Amazon S3,
focusing on how to create, secure, manage, and automate your S3 bucket
operations. You will learn how to configure buckets, upload objects,
enable versioning, apply bucket policies, adjust permissions, and set up
lifecycle rules to optimize storage costs and improve data durability.

S3 is one of the core AWS services for scalable, durable, and secure
object storage --- suitable for backups, application data, media files,
logs, and more.

------------------------------------------------------------------------

## Creating an S3 Bucket

On the AWS Management Console, search for **S3** and click **Create
bucket**.

![](s3_search.png)\
![](create_bucket.png)

Follow the steps:

-   Enter a **unique bucket name**.
-   Set **Object Ownership** to *ACLs disabled*.
-   Keep **Block all public access** enabled.
-   Leave **Bucket Versioning** disabled for now.
-   Keep all other settings at default.

![](bucket_name.png)

Click **Create bucket**.

![](bucket_created.png)

------------------------------------------------------------------------

## Uploading an Object to an S3 Bucket

Create a text file (e.g., `welcome.txt`) and save it locally.

Open your S3 bucket and click **Upload**:

![](click_upload.png)

Choose **Add files**, locate your file, and select **Open**.

![](click_add_files.png)

![](file_uploaded.png)

Click **Upload** to complete the process.

![](upload_success.png)

------------------------------------------------------------------------

## Enabling S3 Bucket Versioning

Versioning allows S3 to keep multiple versions of an object. This
protects against overwriting, accidental deletions, or application
errors.

Go to your bucket → **Properties** → **Bucket Versioning**.

![](enable_versioning.png)

Select **Enable** and click **Save changes**.

![](versioning_enabled.png)

Upload an updated version of the same file and enable **Show versions**
to view all object versions.

![](show_versions.png)

------------------------------------------------------------------------

## File Permissions in S3

Objects are private by default. To allow access, you must explicitly
change permissions or apply a bucket policy.

Go to your bucket → **Permissions**.

![](bucket_permission.png)

Uncheck **Block all public access**, click **Save changes**, type
*confirm*, and apply your changes.

![](save_permissions.png)

> ⚠️ Be cautious when making buckets public --- only do so when
> necessary and never for sensitive data.

------------------------------------------------------------------------

## Bucket Policy

A **Bucket Policy** defines who can access objects in your bucket and
what actions they can perform.

Open **Bucket Policy** and click **Edit**.

![](bucket_policy_edit.png)

Click **Policy Generator**.

![](policy_gen.png)

If not available, use the standalone generator.

![](policy_gen_tool.png)

Enter these details:

-   **Policy Type**: S3 Bucket Policy\
-   **Effect**: Allow\
-   **Principal**: `*`\
-   **Actions**: `GetObject`, `GetObjectVersion`\
-   **ARN**: your bucket ARN + `/*`

![](policy_gen1.png)\
![](policy_gen2.png)

Generate and copy the policy:

![](generate_policy.png)

Paste it into the bucket policy editor:

![](generated_policy.png)

Save the policy:

![](saved_policy.png)

------------------------------------------------------------------------

## Accessing Bucket Objects

Open your bucket and click on any object version. Copy the object URL
and paste it into a browser.

![](object_url.png)

![](object_accessed.png)

------------------------------------------------------------------------

## Lifecycle Policies

Lifecycle rules help automate storage transitions, cleanup, and cost
optimization. You can automatically move objects to cheaper storage
classes or delete them after a certain period.

Go to **Management** → **Create lifecycle rule**.

![](lifecycle_rule.png)

Fill in the rule details:

![](lifecycle_params1.png) ![](lifecycle_params2.png)
![](lifecycle_params3.png)

Click **Create rule**.

![](lifecycle_success.png)

Your lifecycle rule is now active. In this example, objects transition
to **Standard-IA** after 30 days --- reducing storage costs for
infrequently accessed files.

------------------------------------------------------------------------

## Conclusion

Amazon S3 provides a flexible, secure, and scalable way to store and
manage your data. By learning how to create buckets, upload content,
enable versioning, modify permissions, apply bucket policies, and
automate lifecycle transitions, you gain the foundational skills needed
to work confidently with cloud storage. These techniques improve data
reliability, optimize costs, and give you greater control over your
cloud resources. As you advance, you can explore encryption,
replication, event notifications, and integrations with other AWS
services to deepen your cloud expertise.

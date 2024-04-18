# S3 Bucket Policy for CloudFront Access

## Purpose

In this mini project, you will configure an S3 bucket policy that allows access only from a specific CloudFront distribution. This ensures that your S3 content is securely served through CloudFront, and direct access to the S3 bucket is restricted.

## Objectives

1. **Create an S3 Bucket**:

   - Learn how to create an S3 bucket in the AWS Management Console.

2. **Configure Static Website Hosting**:

   - Set up the S3 bucket for static website hosting.

3. **Create a CloudFront Distribution**:

   - Learn how to create a CloudFront distribution.

4. **Configure S3 Bucket Policy**:

   - Implement a bucket policy that allows access only from the CloudFront distribution.

5. **Test Access Restrictions**:
   - Verify that direct access to the S3 bucket is restricted, and content is accessible only via CloudFront.

## Setting Up Amazon CloudFront for Secure Content Delivery: A Step-by-Step Guide

## Overview

In this guide, we'll walk through the process of creating an Amazon S3 bucket and configuring Amazon CloudFront for secure content delivery. By following these steps, you'll ensure that your static website content is efficiently distributed through CloudFront while restricting direct access to the S3 bucket.

## Step 1: Create an Amazon S3 Bucket

1. **Log in to your AWS Management Console**.
2. Navigate to the **Amazon S3** service from the service list.
3. Click on **"Create bucket"** if you don't already have an S3 bucket.
4. Specify a **DNS-compliant bucket name** (e.g., `my-static-website-bucket`).
5. Choose the **Region** where your bucket should be located (e.g., `us-west-1`).
6. Upload bucket with the website_files.

## Step 2: Create a CloudFront Distribution

1. Go to **CloudFront** from the **Networking & Content Delivery** section in the AWS console.
2. If you've previously accessed CloudFront, it may appear in your history for quicker access. Otherwise, click on **"Create Distribution"**.
3. Configure the following settings:
   - **Origin Domain Name**: Enter the Amazon S3 endpoint for your bucket (e.g., `my-static-website-bucket.s3.us-west-1.amazonaws.com`).
   - If your S3 bucket is in the same AWS account, it should show up in the dropdown list. If it's in a different account, ensure proper permissions for CloudFront to access the bucket.
   - Optionally, specify an **origin path** if your objects are organized within subfolders.
   - Note: You don't need to enable static website hosting on your bucket; CloudFront will use the REST API endpoint of the bucket as the origin.

## Step 3: Configure Origin Access

- Implement a bucket policy that allows access only from the CloudFront distribution.

  **Configure either OAC or OAI for the distribution using the REST API endpoint.**
  Use a REST API endpoint as the origin, and restrict access with an origin access control (OAC) or origin access identity (OAI)
  Note: It's a best practice to use origin access control (OAC) to restrict access. Origin access identity (OAI) is a legacy method for this process.

## Step 4: Additional Configuration Steps

1. **Configure Default Cache Behavior**:

   - Under **"Default Cache Behavior Settings,"** you'll find options related to cache behavior, viewer settings, cache keys, and origin requests. For now, leave these settings as default.

2. **Function Associations (Optional)**:

   - This step is optional. You can leave it as default unless you have specific requirements.

3. **Web Application Firewall (WAF)**:

   - Select **"Do not enable security protections"** for now. You can configure WAF rules later if needed.

4. **Price Class**:

   - Leave the **Price Class** set to **"Use All Edge Locations"** (Best Performance).

5. **Other Distribution Settings**:

   - **SSL Certificate**: This is optional; you can configure it based on your needs. Leave as default for now.
   - **Default Root Object**: Enter the name of your index document (e.g., `index.html`). Make sure it matches your static website's index document.
   - **Logging**: Set logging to **"Off"** for now.

6. **Create Distribution**:

   - Click **"Create Distribution."**

7. **Verify Your Distribution**:

- Check the status of the distribution in the CloudFront console. If it shows **"InProgress,"** the distribution is not yet fully deployed.
- After deployment, record the value of the **Domain Name** shown in the CloudFront console (e.g., `dj4p1rv6mvubz.cloudfront.net`).
- Test the distribution in a web browser to ensure it's work

Remember to follow best practices and regularly review and update your configurations to maintain a secure and efficient distribution.

## Observations and Challenges

During the project, the following observations and challenges were encountered:

1. Understanding the nuances between OAC and OAI for origin access.
2. Understanding the difference between Website endpoints and REST APT endpoints.
3. Ensuring correct permissions and policies for CloudFront access to the S3 bucket.
4. Verifying the functionality and accessibility of the CloudFront distribution after deployment.

## Testing Access Restrictions

- Access restrictions were tested to ensure that the direct access to the S3 bucket was restricted and content is accessible only via CloudFront.

## Insights Gained

1. CloudFront improves content delivery speed and security by caching content at edge locations.
2. OAC provides more granular control over access permissions compared to OAI.
3. Effective use of bucket policies enhances security by defining access rules.
4. You don't need to turn on static website hosting on your bucket for this configuration. This configuration uses the REST API endpoint of the bucket instead of the website endpoint from the static website hosting feature.
5. The key differences between a website endpoint and a REST API endpoint.

## Significance of Securing S3 Content through CloudFront

- **Reduced Attack Surface**: Restricting direct S3 access minimizes exposure to potential threats. CloudFront acts as a protective shield.

- **Improved Latency**: Content served from edge locations reduces latency, enhancing user experience.

- **Compliance and Auditing**: Bucket policies allow fine-grained control over who can access content. Compliance requirements can be met by enforcing specific policies.

## Role of Bucket Policies in Access Control

- **Granular Permissions**: Bucket policies define who can perform specific actions (e.g., read, write) on objects within the bucket. They allow fine-tuning access based on various conditions.

- **Cross-Account Access**: Bucket policies enable granting access to CloudFront distributions in different AWS accounts while maintaining security.

- **Security Best Practices**: Regularly reviewing and updating bucket policies ensures alignment with security best practices.

Remember, securing S3 content through CloudFront is not a one-time setup; it requires continuous monitoring and adjustments to maintain an optimal balance between security and usability.

## Conclusion

Securing S3 content through CloudFront access is essential for performance, security, and scalability. Bucket policies play a vital role in access control, allowing you to define fine-grained permissions. Regularly review and update your configurations to maintain a secure and efficient distribution.

---

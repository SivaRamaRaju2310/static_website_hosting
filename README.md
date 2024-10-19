

# Static Website Hosting with Amazon S3

This project demonstrates how to host a static website using Amazon S3. The website consists of HTML, CSS, and JavaScript files and is served directly from an S3 bucket.

## Prerequisites
- AWS account
- Basic knowledge of HTML, CSS, and JavaScript
- (Optional) AWS CLI for advanced configurations

## Steps to Host the Website

### 1. Create an S3 Bucket
1. Log in to the AWS Management Console.
2. Navigate to **S3** service and click **Create bucket**.
3. Enter a unique bucket name (e.g., `my-static-website`) and choose your AWS region.
4. Keep other settings as default and click **Create bucket**.

### 2. Upload Website Files
1. Go to the newly created S3 bucket.
2. Click **Upload** and add your website files (e.g., `index.html`, `styles.css`).
3. Click **Upload** to complete the process.

### 3. Configure the Bucket for Static Website Hosting
1. In the bucket, go to the **Properties** tab.
2. Scroll to **Static website hosting** and click **Edit**.
3. Enable static website hosting and specify `index.html` as the index document.
4. Optionally, add an error document (e.g., `error.html`).
5. Save the changes.

### 4. Set Bucket Policy for Public Access
1. In the **Permissions** tab, edit the **Bucket policy**.
2. Use the following policy to allow public read access:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::my-static-website/*"
        }
    ]
}
```
Replace `my-static-website` with your bucket name. Save the policy.

### 5. Access the Static Website
1. In the **Properties** tab, under **Static website hosting**, find the **Bucket website endpoint**.
2. Open the URL to view your live website.

## Optional Enhancements
1. **Custom Domain with Route 53** – You can map your S3 bucket to a custom domain.
2. **HTTPS with CloudFront** – Use CloudFront to serve your website over HTTPS with an SSL certificate.

## Example Files
- **index.html**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Static Website</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Welcome to My Static Website</h1>
    <p>This is a simple static website hosted on Amazon S3.</p>
</body>
</html>
```

- **styles.css**
```css
body {
    font-family: Arial, sans-serif;
    text-align: center;
    margin-top: 50px;
}
h1 {
    color: #333;
}
p {
    color: #666;
}
```

## Conclusion
By following this guide, you’ve successfully hosted a static website on AWS S3. Enhance your setup by adding a custom domain and HTTPS for security.

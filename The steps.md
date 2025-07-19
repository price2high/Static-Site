The steps to complete the project can be found on this page
---
# Part 1: 
### Step 1: 
Create your site files: 
1. index.html
2. style.css
3. and a script.js
---
Include your Contact From code in the index.html file. 
In ```script.js``` intercept the form submit and send it via ```fetch()``` to your API endpoint.
### Step 2: Host on AWS S3 (Static Website Hosting)
  1. Sign in to your AWS Console -> go to S3
  2. Click Create bucket
  3. Give your bucket a unique name
  4. choose a region(stick with one region for everything)
  5. Under Block Public Access settings, uncheck “Block all public access.”
 ✅ Important: confirm the warning that this bucket will be public.
  6. Click create bucket
### Step 3: Enable static website hosting
After the Bucket is created: 
  1. Open your bucket → go to the Properties tab.
  2. Scroll all the way down to Static website hosting.
  3. Click Edit.
  4. Select Enable.
  5. Choose Host a static website.
  6. Enter:
    - Index document: index.html
    - (Optional) Error document: error.html (or leave blank).
  7. Click Save changes.
### Step 4: Upload your website files
  1. Go to the Objects tab of your bucket.
  2. Click Upload → Add files (your index.html, script.js, style.css, etc.).
  3. Click Upload.
### Step 5: Make Files public
For static hosting to work: 
  1. Go to your bucket in the AWS Console.
  2. Click the Permissions tab.
  3. Scroll down to Bucket policy and click edit.
  4. Paste a policy like this (replace ``` YOUR_BUCKET_NAME``` with your actual bucket name:
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
    }
  ]
}
```
  5. click save changes.
# ✅ Now every object you upload to that bucket will be publicly readable.
---
### Step 5: Test your site
  1. Go back to Properties -> static website hosting
  2. Copy the Bucket website endpoint
     (ie ```http://my-portfolio-site.s3-website-us-east-1.amazonaws.com```)
  3. Paste it in your browser- you should see your index.html
---
# Part 2: 
 ### Step 1: Set up SES (simple email service)
If you don't have youre own domain yet:
  1. in SES -> go to Verified Identities-> Create identity.
  2. Choose email address.
  3. Enter a valid email you own
  4. SES will send a verfication link to that email. click the link.
✅ After that, you can use that verified email as the Source (the “From” address) in your Lambda code:

``` Source='yourname@gmail.com' ```
### Step 2: Creat your lambda function
We'll use Python.
  1. Go yo lambda console -> create function.
  2. Choose Author from scratch:
       - Name: ContactFormHandler
       - Runtime: Python3.9 (or latest available)
  3. Click Create function.
  4. Add basic permissions:
       - Go to Configuration -> Permissions
       - Click the role name under Execution role -> this open IAM
       - add permisisons -> attach policies
       - attach the policy AmazonSESFullAccess
  5. Open Lambda Code
  6. In the lambda console enter:
```
import json
import boto3
import os
ses = boto3.client('ses', region_name='us-east-1')  # change region if needed
def lambda_handler(event, context):
    try:
        body = json.loads(event['body'])
        name = body.get('name', 'No name')
        email = body.get('email', 'No email')
        message = body.get('message', 'No message')
        # Build email
        response = ses.send_email(
            Source='your-verified-email@example.com',  # Must be verified in SES
            Destination={
                'ToAddresses': ['your-destination-email@example.com']
            },
            Message={
                'Subject': {
                    'Data': f'New contact form message from {name}'
                },
                'Body': {
                    'Text': {
                        'Data': f"Name: {name}\nEmail: {email}\nMessage:\n{message}"
                    }
                }
            }
        )
        return {
            'statusCode': 200,
            'headers': {
                'Access-Control-Allow-Origin': '*',
                'Access-Control-Allow-Headers': '*',
                'Access-Control-Allow-Methods': 'OPTIONS,POST'
            },
            'body': json.dumps({'message': 'Email sent successfully!'})
        }
    except Exception as e:
        print(f"Error: {e}")
        return {
            'statusCode': 500,
            'headers': {
                'Access-Control-Allow-Origin': '*'
            },
            'body': json.dumps({'error': 'Failed to send email.'})
        }
```
  7. Make sure to update your verfied email in the code above.
### Step 3: Create API Gateway: 
  1. Go to API Gateway Console -> Create API.
       - Choose rest API -> Build
  2. Choose New API
       - Name: ContactFormAPI
       - Endpoint type: Regional
       - Click Create API
  3. In your new API, Click Actions -> Create Resource:
       - Resource name: Contact
           The /contact path will fill in after you save the resource.
       - Resource path: /contact
       - Click Create Resource
  4. With /contact selected , click actions -> create method:
       - Choose POST -> In the "Method Type" Drop down.
  5. Integration type: Lambda Function
       - Region: your Lambda's region
       - Lambda function: ContactFormHandler
       - Save -> confirm permissions
### Step 4: Enable CORS on API Gateway
  1. Select the /contact on the resource tab -> Enable CORS
  2. Check both:
       a. OPTIONS (preflight requests)
       b. Post (your form submission)
### Step 5: Deploy API
  1. Actions -> Depoly API
  2. Deployment Stage: [New Stage] -> name it prod.
  3. Click Deploy.
You'll get an invoke URL (IE):
``` https://abc123.execute-api.us-east-1.amazonaws.com/prod/contact```
✅ That is the endpoint your static site will call in script.js.
### Step 6: Test the Flow
 - Update your script.js in your static site to use the Invoke URL from above.
 - Upload the updated file to S3.
 - Open your static site-> fill out form -> submit.
 - check the destination email inbox.
✅ You should receive the email within a few seconds!

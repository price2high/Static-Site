# 🚀 Static Website and Serverless Contact Form Project
How can we call ourselves the future of technology and not have a website to match? How can we not have a contact form that actually forwards contact information directly to our own inboxes? That’s exactly what this Saturday’s AWS project was all about. We set out to build more than just a webpage—we wanted a modern, scalable, serverless solution that reflects the innovation we stand for. The result? A static website hosted on AWS S3, complete with a serverless contact form powered by AWS Lambda, Amazon SES (Simple Email Service), and secure API Gateway calls. This is what it looks like when the future of technology builds for itself

---

## 🏗️ Architecture Overview

**Below is how everything connects:**

1. **User’s Browser**  
   The visitor opens the static website and fills out the contact form.

2. **AWS S3 Static Website**  
   The website is hosted on an S3 bucket and serves the HTML/CSS/JS to the browser.

3. **Amazon API Gateway**  
   When the form is submitted, the frontend sends the data to an API Gateway endpoint.

4. **AWS Lambda**  
   API Gateway triggers a Lambda function that processes the form data.

5. **Amazon SES (Simple Email Service)**  
   Lambda uses SES to send the form data as an email.

6. **Your Inbox**  
   The email arrives directly in your inbox, completing the workflow.

---

## 🔧 What We Used and Why
| Service / Tool | Purpose | Why We Used It |
|----------------|---------|----------------|
| **Amazon S3 (Simple Storage Service)** | Hosts our static website (HTML, CSS, JS). | S3 is cost‑effective, highly available, and perfect for static site hosting. |
| **Amazon API Gateway** | Creates a secure endpoint to receive contact form submissions. | Lets us expose our Lambda function as a REST API without managing servers. |
| **AWS Lambda** | Serverless compute to process form data and trigger SES. | No servers to maintain; runs only when needed, making it scalable and cost‑efficient. |
| **Amazon SES (Simple Email Service)** | Sends emails containing the form submissions to our inbox. | Reliable, integrates directly with Lambda, and supports verified domains. |
| **HTML/CSS/JS** | Frontend of our website. | Clean, responsive UI with a contact form. |
| **IAM Roles & Policies** | Securely control access between services. | Ensures only the right services have permission to send email or access data. |



## ✨ Why This Matters
By combining these services, we built a production‑ready solution without deploying a single traditional server. It scales automatically, costs almost nothing when idle, and showcases exactly what it means to build for the future of technology.


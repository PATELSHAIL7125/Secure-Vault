# 🔐 Secure File Vault – Time-Based Shareable File Storage

![AWS](https://img.shields.io/badge/AWS-Serverless-orange)
![Lambda](https://img.shields.io/badge/AWS%20Lambda-Node.js%2020-blue)
![API](https://img.shields.io/badge/API-Gateway-green)
![Storage](https://img.shields.io/badge/Storage-S3%20Private-yellow)
![Database](https://img.shields.io/badge/Database-DynamoDB-purple)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## 📌 Overview

**Secure File Vault** is a serverless web application that allows users to upload files, generate **time-limited shareable download links**, and securely access files until the link expires.

Once expired, access is immediately blocked without requiring instant file deletion.

This project demonstrates **real-world AWS serverless architecture**, **secure file access control**, and **expiry-based authorization**.

---

## 🚀 Features

- 📤 Secure file upload  
- ⏱️ User-defined link expiry (minutes)  
- 🔗 Shareable download links  
- 📋 Copy link to clipboard  
- ⬇️ One-click file download  
- 🚫 Automatic access blocking after expiry  
- 🔐 Private S3 storage (no public access)  
- 🧹 Automatic cleanup using AWS-managed services  
- 🌐 Simple, clean frontend UI  

---

🏗️ Architecture

### 🔧 Services Used

- **Frontend:** HTML, CSS, JavaScript  
- **Backend:** AWS Lambda (Node.js 20)  
- **API Layer:** Amazon API Gateway (REST)  
- **Storage:** Amazon S3 (Private Bucket)  
- **Metadata Store:** Amazon DynamoDB (TTL Enabled)  
- **Security:** IAM Roles, Presigned URLs, CORS  



---

🔄 Application Flow

### 📤 Upload Flow

1. User selects a file and expiry time  
2. Frontend sends file (Base64) and expiry to API  
3. **Upload Lambda**:
   - Generates a unique `fileId`
   - Uploads file to a private S3 bucket
   - Stores metadata in DynamoDB  
4. API returns a shareable link  

### ⬇️ Download Flow

1. User opens the shareable link  
2. **Download Lambda**:
   - Fetches metadata using `fileId`
   - Validates expiry time
   - Generates a presigned S3 URL  
3. File downloads if link is valid  
4. Access is blocked after expiry  



---

⏳ Expiry & Cleanup Strategy

| Component | Responsibility |
|----------|----------------|
| DynamoDB TTL | Controls access expiry |
| Lambda | Blocks access after expiry |
| S3 Lifecycle | Cleans up files asynchronously |

- **Immediate Security:** Access blocked after expiry  
- **Asynchronous Cleanup:** AWS handles deletion  
- **No Cron Jobs Required**



---
🔐 Security Design

- S3 bucket is **fully private**
- No direct S3 access allowed
- API-controlled file access
- Time-based authorization
- Presigned URLs for secure downloads
- IAM roles with **least-privilege access**



---

📦 Tech Stack (Click to Expand)

- AWS Lambda (Node.js 20)  
- Amazon S3  
- Amazon DynamoDB  
- Amazon API Gateway  
- HTML, CSS, JavaScript  



---

🎯 Use Cases 

- Temporary file sharing  
- Secure document delivery  
- Expiring download links  
- Cloud architecture learning  
- Serverless demos  



---

🏆 Learning Outcome

- Deep understanding of AWS serverless services  
- Secure backend API design  
- Expiry-based authorization logic  
- Cloud cost optimization  
- Real-world deployment experience  



---
🚀 Future Enhancements 

- Password-protected links  
- One-time download support  
- Countdown timer UI  
- Drag & drop uploads  
- CloudFront CDN  
- Custom domain support  
- Authentication using Amazon Cognito  


---

## 👨‍💻 Author

**Shail Patel**  
B.Tech Student | Cloud & Full-Stack Enthusiast  

---

⭐ *If you found this project useful, feel free to star the repository!*

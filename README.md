🚀 AWS Serverless OTP Authentication System

This project implements a fully serverless OTP verification system using AWS cloud services.
It generates a One-Time Password (OTP), stores it securely using DynamoDB TTL, and sends it via Amazon SES — with no servers to manage.

The frontend is built with Vue.js, and the backend is deployed using AWS SAM.

🧰 Tech Stack
Layer	Technology
Frontend	Vue.js
Backend	AWS Lambda
API Layer	Amazon API Gateway
Database	Amazon DynamoDB (TTL enabled)
Email Service	Amazon SES
Infrastructure-as-Code	AWS SAM
Authentication Flow	Email-based OTP
🏗️ System Architecture

📌 High-level design of the OTP workflow.

architecture.png

🚦 Workflow

User enters their email in the frontend UI.

Frontend calls POST /otp/generate.

Lambda generates OTP and stores it in DynamoDB with TTL.

DynamoDB Stream triggers a second Lambda.

Second Lambda sends OTP via SES.

User enters OTP → Frontend sends request to /otp/verify.

OTP is validated against DynamoDB.

📁 Project Structure
aws-serverless-otp-system/
│
├── backend/
│   ├── template.yaml
│   ├── generate-otp/
│   ├── verify-otp/
│   └── send-email/
│
├── frontend/
│   ├── src/
│   ├── public/
│   ├── .env.example
│   └── package.json
│
└── README.md

📦 Deployment — Backend (AWS SAM)
cd backend
sam build
sam deploy


Make sure SES sender & receiver emails are verified if using Sandbox mode.

💻 Running the Frontend
cd frontend
npm install
npm run serve


Create .env file (based on .env.example):

VUE_APP_API_BASE_URL=https://<your_api_id>.execute-api.<aws-region>.amazonaws.com/dev/otp

🔐 IAM Roles Required
Service	Permission
Lambda logging	AWSLambdaBasicExecutionRole
DynamoDB	AmazonDynamoDBFullAccess
SES Email	AmazonSESFullAccess
🧪 Testing via curl
curl -X POST "<YOUR_API_URL>/otp/generate" \
  -H "Content-Type: application/json" \
  -d '{"email":"your_email@example.com"}'


Expected response:

{"message":"OTP generated","sessionId":"<UUID>"}

🎓 What This Project Demonstrates

Deploying serverless architecture with AWS SAM

Event-driven processing using DynamoDB Streams

Triggering transactional email using AWS SES

Integrating AWS backend with a modern frontend framework (Vue.js)

🚀 Future Enhancements

SMS delivery using AWS SNS

Multi-factor authentication support

Throttling & rate-limiting with API Gateway

CI/CD using GitHub Actions or Jenkins

📌 Status
Feature	Status
API Deployment	✅
OTP Generation	✅
DynamoDB Storage + TTL	✅
SES Email Delivery	✅
UI Integration	✅
⭐ Contribute

⭐ Star the repository

🐛 Open an issue

🛠️ Submit a pull request

👤 Author

Amal Siby
Cloud & DevOps Enthusiast ☁️
📫 Email / LinkedIn link optional

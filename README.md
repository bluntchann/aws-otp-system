# AWS Serverless OTP System

A serverless OTP (One-Time Password) system built with:

- AWS Lambda
- Amazon API Gateway
- Amazon DynamoDB
- Amazon SES
- AWS SAM
- Vue.js frontend

## Features

- Generate OTP and store in DynamoDB with TTL
- Send OTP via Amazon SES
- Simple Vue.js UI to request and verify OTP
- Uses AWS SAM for backend deployment

## Backend (SAM)

```bash
cd backend
sam build
sam deploy

## Frontend
cd frontend
npm install
npm run serve

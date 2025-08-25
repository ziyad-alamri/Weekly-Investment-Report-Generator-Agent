# 📊 Weekly-Investment-Report-Generator-Agent



## 📝 Problem Statement
As Investor I often don’t have enough time to keep track of my investments up-to-date news, or market movements. Sometimes I even forget to check them regularly.  
This project solves that by creating an **Agentic AI** that fetches stock data weekly, generates a readable **AI-based summary report**, and sends it directly via **email**.

---

## 🏗️ Solution Overview
The system uses **AWS serverless services** and **Polygon.io** to collect stock market data and news, process it with an **AI model (Amazon Bedrock – Claude 3 Sonnet)**, and deliver a **weekly report**.

---

## 🔑 AWS Services Used

- **Amazon EventBridge** → Schedules the weekly execution.  
- **AWS Secrets Manager** → Stores the Polygon.io API key securely.  
- **Amazon DynamoDB** → Stores companies and their stock symbols.  
- **Polygon.io** → Provides stock market data (real-time & historical).  
- **Amazon Bedrock (Claude 3 Sonnet)** → Generates AI-powered natural language reports.  
- **Amazon S3** → Stores generated reports as archives.  
- **Amazon SES (Simple Email Service)** → Emails the report to the investor.  

---

## ⚙️ Workflow
1. **EventBridge** triggers **Lambda** on schedule.
2. **Lambda**:
   - Reads stock symbols from **DynamoDB**.
   - Gets the **Polygon.io API key** from **Secrets Manager**.
   - Fetches stock data from **Polygon.io**.
   - Passes the raw data to **Bedrock** for summarization.
   - Stores the summary in **S3**.
   - Emails the summary to me using **SES**.
3. I receive a **weekly investment summary** in my inbox 🎉.

---

## 🔒 Security
- **Secrets Manager** ensures API keys are not exposed.
- **IAM roles** give Lambda only the permissions it needs.
- **SES sandbox mode** ensures controlled testing before production.

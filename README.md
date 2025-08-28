# 📩 Lead Capture Flow (n8n + OpenAI)

This project is an **automated lead management workflow** built with [n8n](https://n8n.io).  
It captures form submissions from a website, classifies them with AI, scores their urgency, and sends clean email notifications.  

---

## ⚙️ Workflow Overview
1. **Webhook** → receives form submissions (Name, Email, Phone, Message).  
2. **Edit Fields** → normalizes input data.  
3. **AI Classifier (OpenAI)** → classifies message into:
   - **Lead**: sales-related  
   - **Support**: help-related  
   - **Spam**: irrelevant  
4. **Lead Scoring**:
   - 🔥 **Hot** → strong buying intent (e.g., "I want bulk pricing today").  
   - 🌡 **Warm** → interested, less urgent (e.g., "I’d like more info").  
   - ❄️ **Cold** → vague, low intent, or spam.  
5. **Spam Filter** → discards spam.  
6. **Email Notification** → sends structured details to your inbox.

---

## 🚀 Setup Instructions

### 1️⃣ OpenAI API Key
- Open **OpenAI Chat Model** node → create credential → paste your API Key.  
- [n8n OpenAI documentation](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-langchain.openai/)

### 2️⃣ SMTP Credentials
- Open **Send Email** node → create credential:  
  - **User**: your email (e.g., `example@gmail.com`)  
  - **Password**: Google App Password ([guide](https://myaccount.google.com/apppasswords))  
  - **Host**: `smtp.gmail.com`  
  - **Port**: `465`  
- Then set **From Email** and **To Email**.

### 3️⃣ Webhook URL
Default path:  https://<your-n8n-host>/webhook/lead-capture
To confirm, open the **Webhook** node → check **Production URL** (don’t use the Test URL).  

### 4️⃣ Expected Payload
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "+447000000000",
  "message": "Hi, I want bulk pricing for your product."
}


# 📩 Lead-Capture Flow — Setup Guide

## 1️⃣ Add Your OpenAI API Key
1. Open the **OpenAI Chat Model** node in this workflow.  
2. In the field below **“Credential to connect with”**, click **Create new credential**.  
3. Enter your API key in the **API Key** field.  
4. For help getting your API key, see n8n’s OpenAI documentation.

---

## 2️⃣ Add Your SMTP Email Credentials
1. Open the **Send Email** node.  
2. In the field below **“Credential to connect with”**, click **Create new credential**.  
3. In **User**, enter the email address you’re sending from (e.g., `example@domain.com`).  
4. In **Password**, enter your **Google App Password**:
   - Sign in to your Google Account: [https://myaccount.google.com/](https://myaccount.google.com/)  
   - Enable **2-Step Verification** (if not already enabled).  
   - Go to: [https://myaccount.google.com/apppasswords](https://myaccount.google.com/apppasswords)  
   - Create a new app password (name it something like `n8n credential`), click **Create**, then copy the password shown.  
   - Paste this app password into the **Password** field.
5. In **Host**, enter: `smtp.gmail.com`  
6. In **Port**, enter: `465`  
7. Save the credentials.  
8. In the **Send Email** node, set:
   - **From Email**: the same email you added in credentials.  
   - **To Email**: where you want to receive the leads.

---

## 3️⃣ Webhook URL & Expected Payload
- **Default webhook path**:  
```
https://<your-n8n-host>/webhook/lead-capture
```
- **Check your actual webhook URL**:
  1. Open the **Webhook** node.  
  2. Look under **Webhook URLs**.  
  3. Use the **Production URL** (not the Test URL).  
  4. This will show your correct URL based on your n8n setup.

- **Expected JSON Payload**:
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "+447000000000",
  "message": "Hi, I want bulk pricing for your product."
}
```

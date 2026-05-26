# 📖 Step-by-Step Setup Guide

This guide walks you through setting up the Mental Health Chatbot. No prior experience needed!

---

## 🛠️ What You Need Before Starting

| Tool | Why You Need It | Where to Get It |
|---|---|---|
| n8n | The platform that runs the chatbot | [n8n.io](https://n8n.io) |
| OpenAI API Key | Powers the AI responses | [platform.openai.com](https://platform.openai.com) |
| Pinecone (free) | Stores the WHO document data | [pinecone.io](https://pinecone.io) |

---

## 📥 Step 1 — Import the Workflow into n8n

1. Go to your n8n dashboard
2. Click **"Workflows"** in the left menu
3. Click **"New Workflow"**
4. Click the three dots menu **(⋮)** in the top right
5. Select **"Import from file"**
6. Upload the file: `workflow/mental-health-chatbot.json`
7. Click **"Save"**

---

## 🔑 Step 2 — Add Your API Keys

### OpenAI Key
1. In n8n, go to **Settings → Credentials**
2. Click **"Add Credential"**
3. Search for **"OpenAI"**
4. Paste your OpenAI API key
5. Click **"Save"**

### Pinecone Key
1. Go to [pinecone.io](https://pinecone.io) and create a free account
2. Create a new Index with:
   - **Dimensions:** 1536
   - **Metric:** cosine
3. Copy your API key
4. In n8n, add a new **Pinecone credential** with this key

---

## 📄 Step 3 — Load WHO Documents (Do This Once Only)

1. Open the **"Setup: Load WHO Documents"** workflow
2. Click **"Execute Workflow"** (the play button ▶)
3. Wait 1–2 minutes for it to finish
4. Once done, all WHO documents are stored and ready ✅

> You only need to do this step ONE time. After that, the chatbot remembers all the WHO data.

---

## 💬 Step 4 — Test the Chatbot

1. Open the **"Mental Health Chat"** workflow
2. Enable the trigger (toggle it ON)
3. Open the chat window
4. Try asking: *"What are the symptoms of depression?"*
5. The chatbot should reply with a WHO-backed answer ✅

---

## 🌐 WHO PDF URLs (Add These to the HTTP Request Node)

```
https://www.who.int/docs/default-source/coronaviruse/mental-health-considerations.pdf

https://www.who.int/docs/default-source/primary-health-care-conference/mental-health.pdf

https://applications.emro.who.int/docs/9789290225652-eng.pdf

https://www.globalfamilydoctor.com/site/DefaultSite/filesystem/documents/resources/MHGuidebook-EBookDownload.pdf

https://www.ilo.org/media/309556/download
```

---

## ❓ Common Problems and Fixes

| Problem | Fix |
|---|---|
| Chatbot gives empty answers | Make sure you ran the Setup workflow first |
| API key error | Double-check your OpenAI key in Credentials |
| Pinecone connection failed | Make sure index dimensions are set to 1536 |
| PDFs not loading | Check your internet — n8n needs to download them |

---

## 🆘 Need Help?

Open an Issue on the GitHub repo and include:
- Which step you are stuck on
- The error message you see
- A screenshot if possible

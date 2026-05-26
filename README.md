# 🧠 Mental Health Chatbot — Powered by WHO Data & n8n

A smart, compassionate mental health chatbot built with **n8n**, **OpenAI GPT**, and **WHO (World Health Organization)** official documents. It answers mental health questions based on real WHO guidelines — not made-up answers.

---

## 💡 What Does This Chatbot Do?

- Answers mental health questions (depression, anxiety, stress, PTSD, etc.)
- Pulls answers directly from WHO PDF documents
- Remembers the conversation context (chat memory)
- Tells users to seek professional help when needed
- Responds in a warm, non-judgmental tone

---

## ⚙️ How It Works — Simple Explanation

The workflow has **2 main parts**:

### Part 1 — Load WHO Documents (Run This Once)
```
Setup Trigger → Fetch WHO PDFs → Split Text → Create Embeddings → Save to Vector Store
```
This part downloads WHO PDF files, breaks them into small chunks, converts them into a searchable format, and saves them to a database.

### Part 2 — Chat with User (Runs Every Time Someone Asks a Question)
```
User Message → AI Agent → Search WHO Knowledge Base → Generate Answer → Reply to User
```
When a user asks a question, the AI searches the WHO database for the right information and gives a helpful, accurate answer.

---

## 🧩 Workflow Nodes Explained

| Node | What It Does |
|---|---|
| **Mental Health Chat** | Receives messages from the user |
| **Mental Health Support Agent** | The AI brain — processes questions and gives answers |
| **OpenAI GPT-5** | The language model that powers the responses |
| **Chat Memory** | Remembers previous messages in the conversation |
| **Agent Memory** | Stores longer-term context for the AI agent |
| **WHO Knowledge Base** | Vector database storing all WHO document data |
| **WHO Document Retriever** | Searches the knowledge base for relevant info |
| **OpenAI Embeddings** | Converts text into a searchable format |
| **Fetch WHO PDF Documents** | Downloads WHO PDFs from official URLs |
| **Load PDF Content** | Reads and extracts text from the PDFs |
| **Split Text** | Breaks large documents into smaller chunks |
| **OpenAI Embeddings for Insert** | Converts chunks into vectors before saving |
| **Insert WHO Documents** | Saves everything into the vector database |

---

## 🚀 How to Set This Up

### Step 1 — What You Need
- [n8n](https://n8n.io) account (cloud or self-hosted)
- OpenAI API key — get it from [platform.openai.com](https://platform.openai.com)
- Pinecone account (free) — get it from [pinecone.io](https://pinecone.io)

### Step 2 — Import the Workflow
1. Download the file `workflow/mental-health-chatbot.json`
2. Open your n8n dashboard
3. Click **"Import from file"**
4. Select the downloaded JSON file
5. Click **Save**

### Step 3 — Add Your API Keys
Go to **Settings → Credentials** in n8n and add:
- `OpenAI API Key`
- `Pinecone API Key`

### Step 4 — Load WHO Documents (Do This Once)
1. Open the **"Setup: Load WHO Documents"** workflow
2. Click **Execute** (the play button)
3. Wait 1–2 minutes for it to finish
4. All WHO documents are now stored and ready ✅

### Step 5 — Start Chatting!
Enable the **Mental Health Chat** trigger and your chatbot is live!

---

## 📄 WHO Data Sources Used

| Document | Topics Covered | Link |
|---|---|---|
| Mental Health & COVID-19 | Stress, Anxiety, Crisis Support | [Open PDF](https://www.who.int/docs/default-source/coronaviruse/mental-health-considerations.pdf) |
| Mental Health in Primary Care | Common Disorders, Treatment | [Open PDF](https://www.who.int/docs/default-source/primary-health-care-conference/mental-health.pdf) |
| Mental Health in Schools | Anxiety, PTSD, Student Health | [Open PDF](https://applications.emro.who.int/docs/9789290225652-eng.pdf) |
| Mental Health Care Guide | Depression, OCD, Suicide, Substance Use | [Open PDF](https://www.globalfamilydoctor.com/site/DefaultSite/filesystem/documents/resources/MHGuidebook-EBookDownload.pdf) |
| WHO Mental Health Introduction | Stress, Workplace Mental Health | [Open PDF](https://www.ilo.org/media/309556/download) |

---

## 🤖 AI Agent System Prompt

Paste this into the **System Prompt** field of your AI Agent node:

```
You are a compassionate mental health support assistant trained on WHO (World Health Organization) guidelines and resources.

Your role:
- Answer mental health questions clearly and kindly
- Base your answers on the WHO documents provided to you
- Use simple, easy-to-understand language
- Always be supportive and non-judgmental

Rules:
- Only answer questions related to mental health
- If the answer is in the provided WHO documents, use that information
- If you do not know the answer, say: "I am not sure about that. Please consult a mental health professional or visit who.int for more information."
- Never diagnose any medical condition
- Always remind users to seek professional help for serious concerns
- If someone seems to be in crisis, always say: "If you are in crisis, please contact your local emergency services or a crisis helpline immediately."

Tone: Warm, calm, and supportive — like a caring guide, not a doctor.
```

---

## 🔒 Safety Rules Built In

- ❌ Will NOT diagnose any medical condition
- ❌ Will NOT give specific medication advice
- ✅ Always recommends seeing a professional for serious concerns
- ✅ Immediately provides crisis resources if someone is in danger
- ✅ Only answers from verified WHO documents

---

## 📁 Repo Structure

```
mental-health-chatbot/
│
├── README.md                        ← You are here
├── LICENSE                          ← MIT License
├── CONTRIBUTING.md                  ← How to contribute
├── workflow/
│   └── mental-health-chatbot.json  ← Import this into n8n
├── docs/
│   └── setup-guide.md              ← Detailed setup instructions
└── assets/
    └── workflow-preview.png        ← Screenshot of the workflow
```

---

## 🙋 Who Is This For?

- Developers building mental health tools
- Students learning about AI chatbots and n8n
- Health organizations wanting a WHO-backed chatbot
- Anyone curious about RAG (Retrieval-Augmented Generation) workflows

---

## ⚠️ Disclaimer

This chatbot is for **informational purposes only**. It is NOT a substitute for professional mental health advice, diagnosis, or treatment. If you or someone you know is in crisis, please contact a licensed mental health professional or emergency services immediately.

---

## 📜 License

MIT License — free to use, modify, and share.

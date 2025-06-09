

# 💼 LinkedIn Content Creator Workflow

This n8n workflow automatically generates **professional, inspiring LinkedIn posts** based on two online articles. It is designed for job seekers in **data analysis and HR** to help them grow their LinkedIn presence and attract the attention of potential employers.

---

## 🚀 Features

* ⏰ **Scheduled or manual execution**
* 🔎 Pulls two new articles with a specific status from Google Sheets
* 🌐 Fetches content via Tavily API (or similar search API)
* 🧠 Uses an AI Agent with OpenAI (GPT-4o-mini) to generate engaging, relevant posts
* ✅ Updates Google Sheets with the final LinkedIn-ready post
* 📣 Optimized to appeal to HR and data analysis professionals

---

## 🔧 Setup Instructions

### 1. 📋 Prerequisites

* [ ] An [n8n](https://n8n.io/) instance
* [ ] A Google Sheet with a list of article topics and a **"Status"** column (`To Do`, `created`, etc.)
* [ ] A Tavily API key (or similar web search API)
* [ ] OpenAI API key (GPT-4o-mini recommended)
* [ ] Credentials set up in n8n:

  * **Google Sheets OAuth2**
  * **OpenAI API**
  * **HTTP Auth** (for Tavily)

### 2. 🔐 Credentials Setup in n8n

#### Google Sheets OAuth2

* Create credentials in Google Cloud Console.
* Enable Google Sheets API.
* Set up redirect URI: `https://<your-n8n-domain>/rest/oauth2-credential/callback`

#### OpenAI API

* Go to [https://platform.openai.com/](https://platform.openai.com/)
* Get your API key and create a credential in n8n using the **OpenAI API** node.

#### HTTP Auth (Tavily)

* Use "Authorization" as the header key and your API key as the value.

---

## 📂 File & Sheet Configuration

Your **Google Sheet** should include at least:

| Topic           | Status | Content                                 |
| --------------- | ------ | --------------------------------------- |
| AI Trends in HR | To Do  | *(empty, to be filled by the workflow)* |

The sheet ID must be inserted in the `Google Sheets` node, and the workflow will update the "Content" column after generation.

---

## ⚙️ How It Works

1. **Trigger**:

   * Can run on a daily schedule (7:00 AM) or be manually triggered.
2. **Fetch Article Topic**:

   * Pulls a row from Google Sheets with `Status = To Do`.
3. **HTTP Request**:

   * Makes a POST request to a search API (Tavily) with the topic to retrieve 2 article summaries.
4. **AI Agent**:

   * Combines the two articles and uses a system prompt to write an inspiring, professional LinkedIn post aimed at HR and data analysts.
5. **Update Sheet**:

   * Marks the status as `created` and inserts the generated content back into the sheet.

---



#  AI-Powered Gmail Classifier & Assistant

> An advanced automation workflow built with **n8n** that uses **OpenAI (GPT-4o)** to declutter your inbox. It automatically classifies incoming emails, summarizes social updates, and drafts context-aware replies.

[![n8n](https://img.shields.io/badge/n8n-Workflow-FF6D5A?style=flat-square&logo=n8n)](https://n8n.io/)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o-412991?style=flat-square&logo=openai)](https://openai.com/)
[![Gmail](https://img.shields.io/badge/Gmail-Integration-EA4335?style=flat-square&logo=gmail)](https://mail.google.com/)
[![Google Sheets](https://img.shields.io/badge/Google%20Sheets-Logging-34A853?style=flat-square&logo=googlesheets)](https://www.google.com/sheets/about/)

##  Overview

This workflow is designed to solve the "inbox anxiety" by acting as an intelligent middleman. It processes every incoming email in real-time and routes it based on semantic analysis, ensuring that you only focus on what truly matters.

##  Key Features

###  Intelligent Classification
Uses `gpt-4o-mini` via LangChain to categorize emails into 7 distinct types:
* **Promotions / Receipts:** Automatically marked as read.
* **Social:** Summarized and logged to Google Sheets, bypassing the inbox.
* **Personal / Sales / Recruitments:** Prioritized for drafting.

###  Smart Auto-Drafting
For high-priority categories, the workflow uses `gpt-4o` to generate:
* **Context-Aware Replies:** Drafts that match the tone of the sender.
* **Human-in-the-loop:** All replies are saved as **Drafts**, allowing you to review before sending.

###  Social Summary Logging
Never miss a social update without cluttering your inbox. Summaries are logged in a structured format in **Google Sheets** with timestamps.

##  Tech Stack

* **Workflow Engine:** n8n (Self-hosted/Cloud)
* **AI Models:** * `gpt-4o-mini` (Fast & Efficient Classification)
   * `gpt-4o` (High-Quality Drafting & Summarization)
* **Integrations:** Gmail API, Google Sheets API, LangChain.

##  Setup & Configuration

### 1. Prerequisites
* An active **n8n** instance.
* **OpenAI API Key** (GPT-4o access).
* **Google Cloud Console** project with Gmail and Google Sheets APIs enabled.

### 2. Installation
1.  Download the `Gmail_Classifier.json` file.
2.  In your n8n dashboard, click **"Import from File"** and select the JSON.

### 3. Configuration (Critical Steps)
To make this workflow yours, update the following nodes:
* **Credentials:** Connect your own `Gmail OAuth2` and `OpenAI API` credentials.
* **Google Sheets Node:** Select your specific Spreadsheet and Sheet ID.
* **Labels:** Create labels like `CATEGORY_SOCIAL` and `CATEGORY_PERSONAL` in Gmail or update the nodes to match your existing labels.
* **Customization:** Open the OpenAI nodes and update the system prompt signature (e.g., replace *"Best, Sedat"* with your own name).

## 📝 Usage
Once activated, the workflow polls your inbox every minute:
- **Social emails?** Check your connected Google Sheet.
- **Personal/Work emails?** Check your **Drafts** folder for AI-generated responses.

\# 📧 AI-Powered Gmail Classifier \& Assistant



!\[n8n Workflow View](workflow\_screenshot.jpg)



An advanced automation workflow built with \*\*n8n\*\* that uses \*\*OpenAI (GPT-4o)\*\* to declutter your inbox. It automatically classifies incoming emails, summarizes social updates into Google Sheets, and drafts context-aware replies for personal and professional messages.



\## 🚀 Features



This workflow processes emails every minute and routes them based on their content:



\* \*\*🧠 Intelligent Classification:\*\* Uses `gpt-4o-mini` via LangChain to categorize emails into 7 distinct types: \*Promotions, Social, Personal, Sales, Recruitments, Receipts, and Miscellaneous\*.

\* \*\*🧹 Auto-Triage:\*\*

&nbsp;   \* \*\*Promotions \& Receipts:\*\* Automatically marks as read to keep the inbox clean.

&nbsp;   \* \*\*Social Media:\*\* Summarizes the content and logs it to a \*\*Google Sheet\*\* for later review, skipping the inbox clutter.

\* \*\*✍️ Smart Auto-Drafting:\*\*

&nbsp;   \* \*\*Personal, Sales, \& Recruitment:\*\* Uses `gpt-4o` to generate a polite, context-aware reply draft in Gmail.

&nbsp;   \* \*Safety First:\* It creates a \*\*Draft\*\*; it does not send the email automatically, giving you control to review before sending.

\* \*\*📊 Logging:\*\* Keeps a structured record of social updates in Google Sheets with timestamps and summaries.



\## 🛠️ Tech Stack



\* \*\*Workflow Engine:\*\* \[n8n](https://n8n.io/)

\* \*\*AI Models:\*\* OpenAI `gpt-4o-mini` (Classifier) \& `gpt-4o` (Drafter/Summarizer)

\* \*\*Integrations:\*\* Gmail API, Google Sheets API



\## ⚙️ Setup \& Configuration



\### 1. Prerequisites

\* An active \*\*n8n\*\* instance (Cloud or Self-hosted).

\* \*\*OpenAI API Key\*\* (with access to GPT-4o models).

\* \*\*Google Cloud Console\*\* project with Gmail and Google Sheets APIs enabled.



\### 2. Installation

1\.  Download the `Gmail\_Classifier.json` file from this repository.

2\.  Open your n8n dashboard.

3\.  Click \*\*"Import from File"\*\* and select the JSON file.



\### 3. Configuration (Important)

Since this workflow uses specific IDs from my personal account, you must update the following nodes:



\* \*\*Credentials:\*\* Re-connect your own `Gmail OAuth2` and `OpenAI API` credentials in the respective nodes.

\* \*\*Google Sheets Node:\*\*

&nbsp;   \* Open the "Google Sheets" node.

&nbsp;   \* Select your own Spreadsheet and Sheet ID where you want summaries to be logged.

\* \*\*Gmail Nodes (Labels):\*\*

&nbsp;   \* The workflow applies specific labels (e.g., `CATEGORY\_SOCIAL`, `CATEGORY\_PERSONAL`).

&nbsp;   \* You need to create these labels in your Gmail first, or update the \*\*Gmail Nodes\*\* in n8n to select your own existing labels.

\* \*\*System Prompts:\*\*

&nbsp;   \* Open the OpenAI nodes (OpenAI1, OpenAI2, etc.).

&nbsp;   \* Update the system prompt signature (currently set as \*"Best, Sedat"\*) to your own name.



\## 📝 Usage



Once active, the workflow will poll your inbox every minute.

\- \*\*For Social emails:\*\* Check your connected Google Sheet.

\- \*\*For Personal/Work emails:\*\* Check your Gmail "Drafts" folder for AI-generated replies.



---



\*\*Author:\*\* \[Sedat Aras](https://github.com/sedat4ras)


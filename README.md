# Gmail Classifier — AI-Powered Inbox Automation

> An intelligent email automation workflow built with n8n and GPT-4o that classifies incoming emails, auto-drafts context-aware replies, and logs social summaries to Google Sheets.

[![n8n](https://img.shields.io/badge/Engine-n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white)](https://n8n.io/)
[![OpenAI](https://img.shields.io/badge/AI-GPT--4o-412991?style=flat-square&logo=openai&logoColor=white)](https://openai.com/)
[![Gmail](https://img.shields.io/badge/Integration-Gmail-EA4335?style=flat-square&logo=gmail&logoColor=white)](https://mail.google.com/)
[![Google Sheets](https://img.shields.io/badge/Logging-Google_Sheets-34A853?style=flat-square&logo=googlesheets&logoColor=white)](https://www.google.com/sheets/about/)
[![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)]()

---

## Overview

Gmail Classifier acts as an intelligent middleman for your inbox. It processes every incoming email in real-time using semantic analysis, routes messages based on category, and either auto-drafts replies, marks promotions as read, or logs social summaries — ensuring you only focus on what truly matters.

## Workflow Architecture

```
                         ┌──────────────────┐
                         │   Gmail Inbox    │
                         │   (Poll: 1 min)  │
                         └────────┬─────────┘
                                  │
                         ┌────────▼─────────┐
                         │  GPT-4o-mini     │
                         │  (Classifier)    │
                         └────────┬─────────┘
                                  │
              ┌───────────────────┼───────────────────┐
              │                   │                   │
     ┌────────▼───────┐  ┌───────▼────────┐  ┌───────▼────────┐
     │  Promotions /  │  │    Social      │  │   Personal /   │
     │  Receipts      │  │                │  │   Sales /      │
     │                │  │                │  │   Recruitment  │
     │  → Mark Read   │  │  → Summarize   │  │                │
     │                │  │  → Log to      │  │  → GPT-4o      │
     │                │  │    Sheets      │  │  → Draft Reply │
     └────────────────┘  └────────────────┘  └────────────────┘
```

## Features

### Intelligent Classification
Uses `gpt-4o-mini` via LangChain to categorize emails into 7 distinct types:

| Category | Action |
|----------|--------|
| **Promotions** | Automatically marked as read |
| **Receipts** | Automatically marked as read |
| **Social** | Summarized and logged to Google Sheets |
| **Personal** | AI-drafted reply saved as Draft |
| **Sales** | AI-drafted reply saved as Draft |
| **Recruitment** | AI-drafted reply saved as Draft |

### Smart Auto-Drafting
For high-priority categories, `gpt-4o` generates context-aware replies that match the sender's tone. All replies are saved as **Drafts** — human-in-the-loop review before sending.

### Social Summary Logging
Social updates are summarized and logged to Google Sheets with timestamps, keeping you informed without inbox clutter.

## Tech Stack

| Component | Technology |
|-----------|-----------|
| Workflow Engine | n8n (cloud or self-hosted) |
| Classification | GPT-4o-mini via LangChain (fast + efficient) |
| Draft Generation | GPT-4o (high-quality context-aware replies) |
| Email Integration | Gmail API (OAuth2) |
| Data Logging | Google Sheets API |

## Setup

### Prerequisites

- Active n8n instance
- OpenAI API key (GPT-4o access)
- Google Cloud Console project with Gmail and Google Sheets APIs enabled

### Installation

1. Download `Gmail_Classifier.json` from this repository
2. In your n8n dashboard, click **Import from File** and select the JSON

### Configuration

| Step | Action |
|------|--------|
| **Credentials** | Connect your Gmail OAuth2 and OpenAI API credentials |
| **Google Sheets** | Select your Spreadsheet and Sheet ID in the Sheets node |
| **Gmail Labels** | Create labels like `CATEGORY_SOCIAL` and `CATEGORY_PERSONAL` |
| **Signature** | Update the system prompt signature in OpenAI nodes with your name |

## Usage

Once activated, the workflow polls your inbox every minute:

- **Social emails** — Check your connected Google Sheet for AI summaries
- **Personal/Work emails** — Check your **Drafts** folder for AI-generated responses
- **Promotions/Receipts** — Automatically handled (marked as read)

## Contact

GitHub: [sedat4ras](https://github.com/sedat4ras) | Email: sudo@sedataras.com

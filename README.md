# AI Email Intelligence Agent

An AI-powered email processing and triage system built using n8n that automatically monitors incoming emails, detects spam, categorizes messages, generates summaries, sends Telegram notifications, and logs results to Google Sheets.

---

## Overview

Managing a large number of emails can be time-consuming and inefficient. This project automates the entire email processing pipeline using AI models and workflow automation.

The system continuously monitors a Gmail inbox, analyzes incoming messages for spam, classifies their priority, summarizes the content, and stores the processed information for future reference.

---

## Features

### Email Monitoring
- Automatically watches a Gmail inbox for new messages.
- Retrieves complete email details including subject, sender, and content.

### Spam Detection
Uses a hybrid spam detection approach:

#### CleanTalk API
- External spam intelligence service.
- Detects known spam patterns and malicious senders.

#### Hugging Face RoBERTa Model
- AI-powered spam classification.
- Provides confidence scores for spam detection.

### Email Categorization
Classifies emails into:

- Urgent
- Informational
- Needs Review

using Hugging Face's BART Large MNLI zero-shot classification model.

### Email Summarization
Generates concise summaries using:

- Facebook BART Large CNN

This allows users to quickly understand email content without reading the full message.

### Telegram Notifications
Automatically sends Telegram alerts when:

- An email is classified as Urgent
- An email requires immediate review

### Data Logging
Stores processed email information inside Google Sheets including:

- Subject
- Sender
- Timestamp
- Category
- Spam Status
- Generated Summary

---

## Workflow Architecture

```text
Gmail Inbox
     │
     ▼
Gmail Trigger
     │
     ▼
Email Extraction
     │
     ▼
Spam Detection
 ┌───────────────┐
 │ CleanTalk API │
 │ RoBERTa Model │
 └───────┬───────┘
         │
         ▼
      Decision
         │
 ┌───────┴────────┐
 │                │
 ▼                ▼
Spam         Non-Spam
 │                │
 ▼                ▼
Google      Categorization
Sheets           │
                 ▼
           Summarization
                 │
                 ▼
          Telegram Alerts
                 │
                 ▼
           Google Sheets
```

---

## Tech Stack

| Technology | Purpose |
|------------|----------|
| n8n | Workflow Automation |
| Gmail API | Email Retrieval |
| Hugging Face API | AI Models |
| RoBERTa | Spam Detection |
| BART-Large-CNN | Summarization |
| BART-Large-MNLI | Categorization |
| Telegram Bot API | Notifications |
| Google Sheets API | Data Storage |
| CleanTalk API | Spam Verification |

---

## Sample Output

| Subject | Category | Spam | Summary |
|----------|----------|----------|----------|
| Invoice Due Tomorrow | Urgent | False | Payment required before deadline |
| Weekly Team Meeting | Informational | False | Weekly meeting schedule and agenda |
| Lottery Winner Claim | Spam | True | Suspicious promotional email detected |

---

## Project Structure

```text
AI-Email-Intelligence-Agent/
│
├── workflow/
│   └── ai-email-agent.json
│
├──.gitignore
├── LICENSE
└── README.md
```

---

## Setup

### Prerequisites

- n8n
- Gmail Account
- Hugging Face Account
- Telegram Bot
- Google Sheets Account
- CleanTalk API Key

### Configuration

Configure the following credentials inside n8n:

```env
HUGGINGFACE_API_KEY=
CLEANTALK_API_KEY=
TELEGRAM_CHAT_ID=
GOOGLE_SHEET_ID=
```

Import the workflow JSON file into n8n and connect your credentials.

---

## Use Cases

- Personal Email Management
- Customer Support Automation
- Business Inbox Monitoring
- Priority Email Detection
- Spam Filtering
- Automated Notifications

---

## Future Improvements

- OpenAI/GPT integration
- Sentiment analysis
- Multi-language support
- Email response suggestions
- RAG-based knowledge retrieval
- CRM integration
- Dashboard analytics

---

## Skills Demonstrated

- AI Workflow Automation
- Prompt Engineering
- API Integration
- Email Processing
- Spam Detection Systems
- Text Classification
- Text Summarization
- No-Code / Low-Code Automation
- n8n Development
- Cloud-Based Integrations

---

## Author

**Yashwender Singh**

AI Engineer | Automation Developer | Generative AI Enthusiast

GitHub: https://github.com/Yash-172003

---

## License

This project is licensed under the MIT License.

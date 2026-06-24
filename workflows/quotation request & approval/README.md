# 📄 Quotation Request & Approval Automation — GoHighLevel + AI

When a GoHighLevel contact requests a quote, this drafts a priced quotation document automatically and routes it through a one-line Telegram approval before it ever reaches the client.

## Overview

Two connected n8n workflows handle the full loop: **Quotation Generator**, which fires the moment a contact is tagged in GoHighLevel, and **Approval & Delivery**, which fires when the team replies in Telegram to approve or reject the draft.

## The Problem

Manually pricing a quote, building the document, and logging it in a sheet eats time — and quotes stall whenever the person who normally handles them is busy. AI can draft the quote faster, but an AI-generated quote shouldn't go straight to a client without a human glance first.

## The Solution

### 🧮 Quotation Generator

- A **GoHighLevel webhook** fires when a contact is tagged `request_quotation`, carrying the contact's details.
- An **AI agent** (Google Gemini chat model + structured output parser) analyzes the contact data and extracts everything needed to build the quote.
- Reads the **pricing table** from Google Sheets and counts existing quotations for numbering.
- Copies a quotation template in **Google Drive** and updates the document with the AI-generated pricing details.
- Logs the quotation in a **Google Sheet** database (append or update).
- Sends a **Telegram** message to the team, flagging the quotation for review.

<img width="2265" height="401" alt="image" src="https://github.com/user-attachments/assets/e3361177-44cd-4ae8-8793-7e29ac16dd73" />


### ✅ Approval & Delivery

- A **Telegram trigger** listens for team replies.
- The reviewer replies with a single line: `status docId` (e.g. `approved 1a2b3c`).
- The workflow parses the reply and checks the status.
- If approved: retrieves the client's data from the sheet, downloads the finished quotation document, emails it to the client via **Gmail**, and confirms back in Telegram.

<img width="1608" height="254" alt="image" src="https://github.com/user-attachments/assets/93a22bae-3b00-4115-af35-6893fe3f61b2" />

## The Result

- A quote goes from "contact tagged" to "document drafted and logged" without anyone opening a sheet or a template manually.
- The team keeps full control — nothing reaches a client until someone replies with an approval in Telegram.
- One Telegram message and one reply is the entire human step in the loop.

## Tech Stack

| Tool | Role |
|---|---|
| **GoHighLevel** | Trigger source (contact tagging) |
| **n8n** | Workflow orchestration |
| **Google Gemini** | AI analysis and structured data extraction |
| **Google Sheets** | Pricing table and quotation log |
| **Google Drive** | Quotation template and document storage |
| **Telegram** | Team review request and approval reply |
| **Gmail** | Sending the approved quotation to the client |

## How It Works

```
Quotation Generator:
GHL Webhook (tag: request_quotation) → AI Agent (extract quote data)
   → Read Pricing Table → Copy Template → Update Document
   → Log to Google Sheet → Notify Team via Telegram

Approval & Delivery:
Telegram Reply ("status docId") → Parse Reply → Status check
   → Get Client Data → Download Document → Email to Client
   → Confirm in Telegram
```

## Setup

1. Import both workflow JSONs into your n8n instance: Quotation Generator and Approval & Delivery.
2. In GoHighLevel, configure a workflow that sends a webhook when a contact is tagged `request_quotation`.
3. Connect **Google Sheets** and **Google Drive** credentials, and set up the pricing table and quotation template.
4. Connect a **Google Gemini** credential for the AI agent.
5. Connect a **Telegram Bot** credential to both workflows (notification + reply listener).
6. Connect a **Gmail** credential for sending the final quotation.

---

## Screenshots

> <img width="2289" height="752" alt="image" src="https://github.com/user-attachments/assets/7ebb4869-1a8c-4348-a56e-7983aa648b57" />


### About this project

Built as part of my AI automation portfolio, connected to a GoHighLevel automation. I design systems like this — and direct GHL implementations — for agencies and businesses that want every quote handled consistently, with a human checkpoint instead of full autopilot.

📂 [Full Portfolio](https://canete-jayson-portfolio.lovable.app)

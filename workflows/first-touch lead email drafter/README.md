# ✉️ First-Touch Lead Email Drafter — GoHighLevel + AI

The moment a GoHighLevel form is submitted — new lead, booked consultation, or booked service — this drafts and sends a personalized first-touch email, then flags the team to follow up.

## Overview

A single n8n workflow triggered directly from GoHighLevel form submissions. It logs the contact, routes them by stage, drafts a tailored opening email with AI, sends it, and notifies the team in Slack.

## The Problem

First-touch speed matters, but writing a tailored opening email for every new lead, every booked consultation, and every booked service is repetitive and easy to delay. Generic templates also hurt conversion because they ignore which stage the contact is actually at — a new lead and someone who just booked a paid service shouldn't get the same email.

## The Solution

- A **GoHighLevel trigger** fires on form submission, carrying the contact's data.
- The workflow looks up the contact in a **Google Sheet**: updates the existing row if found, adds a new row if not.
- A **Switch** node routes the contact by type — `new-lead`, `booked-consultation`, or `booked-service` — each mapped to its own prompt.
- An **AI Agent** (Google Gemini chat model, with memory and a structured output parser) drafts a first-touch email tailored to that specific stage.
- Sends the email via **Gmail**.
- Posts a message to the team's **Slack**, flagging the new contact for follow-up.

## The Result

- Every new lead, consultation booking, and service booking gets a tailored first-touch email within moments, not whenever someone gets to it.
- The team gets a Slack heads-up the instant a contact needs human follow-up, instead of relying on someone checking GHL.
- The sheet stays the single source of truth for contact status without manual updates.

## Tech Stack

| Tool | Role |
|---|---|
| **GoHighLevel** | Trigger source (form submissions) |
| **n8n** | Workflow orchestration |
| **Google Sheets** | Contact database |
| **Google Gemini** | Drafting the stage-specific first-touch email |
| **Gmail** | Sending the email |
| **Slack** | Team notification |

## How It Works

```
GHL Form Submission → Lookup/Update Contact in Sheet
   → Switch (new-lead / booked-consultation / booked-service)
   → AI Agent (draft stage-specific email)
   → Send via Gmail → Notify Team via Slack
```

## Setup

1. Import the workflow JSON into your n8n instance.
2. In GoHighLevel, configure the form(s) to trigger this workflow on submission, tagging the contact by stage (new-lead, booked-consultation, booked-service).
3. Connect a **Google Sheets** credential and point it at your contact database.
4. Connect a **Google Gemini** credential to the AI Agent, and confirm each Switch branch's prompt matches the tone you want for that stage.
5. Connect a **Gmail** credential for sending and a **Slack** credential for the team notification.

---

### About this project

Built as part of my AI automation portfolio, connected to a GoHighLevel automation. I design systems like this — and direct GHL implementations — for agencies and businesses that want first-touch outreach to go out instantly and consistently, without anyone manually drafting it.

📂 [Full Portfolio](https://canete-jayson-portfolio.lovable.app)

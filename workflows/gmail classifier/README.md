# 📬 Gmail Classifier — AI-Powered Inbox Triage with n8n

Automatically labels incoming Gmail messages by category using AI classification, then alerts the right person on Telegram the moment a priority email lands.

## Overview

Every new email is checked within a minute of arriving. An AI model reads the subject and body, matches it against categories you define in plain language, and the workflow applies the matching Gmail label no keyword rules, no manual sorting.

## The Problem

Manually sorting and labeling emails wastes time, and rigid keyword filters break the moment a sender phrases something differently. Priority messages new leads, supplier replies, internal requests — get buried in a crowded inbox with no real-time alert.

## The Solution

An n8n workflow that replaces keyword filters with AI-driven classification:

1. **Gmail Trigger** checks the inbox every minute for new messages.
2. **Gemini AI** classifies each email against custom categories (e.g. `new_lead`, `supplier`, `internal`) using natural-language rules instead of fixed keywords.
3. **Gmail label action** applies the matching label automatically.
4. **Telegram alert** notifies the responsible person instantly when a flagged category (e.g. `new_lead`) comes in.

## The Result

- Inbox triage runs unattended, 24/7 — no manual sorting.
- Priority emails surface in real time instead of waiting for the next inbox check.
- Categories are described in plain language, so adding a new one takes minutes, not a rebuild.

## Tech Stack

| Tool | Role |
| **n8n** | Workflow orchestration and scheduling |
| **Gmail** | Email source and labeling |
| **Gemini AI** | Email classification (chat model + classifier) |
| **Telegram** | Real-time alerts to the responsible person |

## How It Works

```
Gmail Trigger (every 1 min)
        ↓
Gemini AI — classifies the email by category
        ↓
Gmail — applies the matching label (new_lead / supplier / internal / ...)
        ↓
Telegram — sends an alert if the category is flagged as priority
```

## Setup

1. Import the workflow JSON into your n8n instance.
2. Connect your **Gmail** account (OAuth2) to both the Trigger and Label nodes.
3. Connect a **Gemini AI** credential and define your categories inside the classifier node's prompt.
4. Connect a **Telegram Bot** credential and set the chat ID for alerts.
5. Activate the workflow.

## Screenshots

> <img width="2310" height="802" alt="image" src="https://github.com/user-attachments/assets/847f284e-831f-48e8-983a-65888fa566fe" />

---

### About this project

Built as part of my AI automation portfolio. I build systems like this — and GoHighLevel implementations — for businesses that want leads, follow-ups, and inbox management running without manual effort.

📂 [Full Portfolio](https://canete-jayson-portfolio.lovable.app)

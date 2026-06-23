 📊 Finances Tracker — AI Expense Logging via Telegram

Send a text, photo, or voice note to a Telegram bot and get your spending analyzed, classified, and summarized — no spreadsheet, no manual entry.

## Overview

The Finances Tracker turns Telegram into a finance-logging interface. Send a message in any format — typed, a photo of a receipt, or a voice note — and an AI agent reads it, classifies the expense, and replies in the same chat with a summary.

<img width="2130" height="995" alt="image" src="https://github.com/user-attachments/assets/2f590ffe-e1f7-4ef0-99bc-0855fbdb8a54" />

## The Problem

Manual expense tracking dies the moment it requires opening an app or a spreadsheet after every purchase. Most people abandon it within a week because logging a transaction is more friction than it's worth.

## The Solution

An n8n workflow that meets the user where they already are — Telegram:

🧠 **Main Workflow**
- Listens for incoming Telegram messages (text, image, or audio).
- Passes the input to an AI agent for financial analysis and classification.
- Sends the summarized result back to the same Telegram chat.

<img width="1972" height="556" alt="image" src="https://github.com/user-attachments/assets/babb8a3f-0427-42c4-aaf9-8e573154ca91" />


🔁 **Sub-Workflow — Media Handling**
- Converts audio messages to text and images (e.g. receipt photos) into an analyzable format.
- Forwards the converted input to the AI agent for the same classification step as a typed message.

<img width="2144" height="368" alt="image" src="https://github.com/user-attachments/assets/31c517a8-992e-4fa2-aa89-e7267faf491c" />


## The Result

- Logging an expense takes one Telegram message — no app switching, no forms.
- Text, voice, and receipt photos are all accepted through the same entry point.
- Classification happens automatically, so the data arrives already organized instead of needing to be sorted later.

## Tech Stack

| Tool | Role |
|---|---|
| **n8n** | Workflow orchestration and automation |
| **Telegram Bot** | User interaction and message handling |
| **Gemini AI** | Chat model, image analysis, and audio analysis |

## Setup

1. Import the workflow JSON into your n8n instance.
2. Create a **Telegram Bot** and connect its credential to the Trigger node.
3. Connect a **Gemini AI** credential to the main workflow and the media-handling sub-workflow.
4. Activate the workflow and message your bot with text, a photo, or a voice note to test.

---

### About this project

Built as part of my AI automation portfolio. I design systems like this — and GoHighLevel implementations — for businesses and individuals who want everyday tasks logged and organized without manual data entry.

📂 [Full Portfolio](https://canete-jayson-portfolio.lovable.app)

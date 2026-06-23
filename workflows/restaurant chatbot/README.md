# 🤖 Reservation Assistant — RAG-Powered Booking Chatbot in n8n

A chat-widget assistant that answers questions from a self-updating knowledge base, checks real calendar availability, and books the reservation end-to-end — no human follow-up required.

## Overview

This project is three connected n8n workflows working as one system: a **Knowledge Base Updater** that keeps the chatbot's answers current, a **Booking Chatbot** that holds the conversation and drives it toward a reservation, and a **Check Availability** tool the chatbot calls to confirm open dates against a live calendar.

## The Problem

Local businesses lose bookings when no one's available to answer a chat message right away. Most chatbots make this worse in one of two ways: they give generic answers because they're not actually connected to the business's real FAQs and policies, or they can hold a conversation but can't book anything — so a human still has to step in to check the calendar and confirm.

## The Solution

### 📥 Knowledge Base Updater

Keeps the chatbot's source of truth current with zero manual data entry:

- **Google Drive trigger** fires when a new file is added to a watched folder.
- Downloads the file and extracts the text (PDF → text).
- Splits the text into chunks.
- An **AI Agent** reads each chunk and extracts structured data: `category` (faq / policy / terms), `question`, `answer`, and `source_file`.
- Generates embeddings via the **Google Generative Language API**.
- Deletes any existing rows tied to that `source_file`, then writes the new structured + embedded rows to **Supabase** — so re-uploading a file refreshes the knowledge base instead of duplicating entries.

> *Screenshot: Knowledge Base Updater workflow*

### 💬 Booking Chatbot

The customer-facing agent, triggered by a webhook from a chat widget:

- Looks up an existing session or creates a new one, so conversation history persists per visitor.
- Retrieves and compresses message history to keep context manageable across long conversations.
- An **AI Agent** (OpenRouter chat model) runs the conversation with three resources:
  - A **Supabase Vector Store** (Google Gemini embeddings + Cohere reranker) for accurate, knowledge-base-grounded answers.
  - The **Check Availability** tool for real-time date checks.
  - Conversation memory.
- Steers the conversation naturally toward booking a reservation rather than just answering questions.
- Once all booking details are collected, it appends the booking to a **Google Sheet**, creates a **Google Calendar** event, and sends a confirmation email — then responds back to the widget.

> *Screenshot: Booking Chatbot workflow*

### 📅 Check Availability (tool sub-workflow)

Called by the Booking Chatbot's AI Agent whenever a customer requests a date or time:

- Adjusts the requested time and pulls matching events from **Google Calendar**.
- Branches depending on whether a conflict exists, checking an adjusted time range if needed.
- Returns the available slot back to the agent to relay to the customer.

> *Screenshot: Check Availability sub-workflow*

## The Result

- A visitor can ask a knowledge-base question and book a reservation in the same conversation, with no manual handling.
- Calendar, spreadsheet, and email all update automatically the moment a booking is confirmed.
- The knowledge base updates itself — dropping a new policy or FAQ document into Google Drive is enough to keep the chatbot's answers current.

## Tech Stack

| Tool | Role |
|---|---|
| **n8n** | Workflow orchestration |
| **Google Drive** | Knowledge base file source |
| **Google Generative Language API** | Text embeddings |
| **Supabase** | Vector store, session, and message history database |
| **OpenRouter** | Chat model for the booking agent |
| **Cohere** | Reranker for vector search results |
| **Google Calendar** | Availability checks and event creation |
| **Google Sheets** | Booking log |
| **Gmail** | Confirmation emails |
| **Chat widget** | Customer-facing interface |

## How It Works

```
Knowledge Base Updater:
Google Drive (new file) → Download → Extract Text → Chunk
   → AI Agent (extract category / question / answer) → Generate Embeddings
   → Delete old rows → Create new rows in Supabase

Booking Chatbot:
Chat Widget → Webhook → Session Lookup/Create → Message History
   → AI Agent (knowledge base + availability tool + memory)
   → Booking complete? → Update Sheet + Create Calendar Event + Send Email
   → Response to Widget

Check Availability (tool):
Requested Date → Adjust Time → Get Calendar Events
   → Conflict? → Adjust + Re-check → Return Available Slot
```

## Setup

1. Import all three workflow JSONs into your n8n instance: Knowledge Base Updater, Booking Chatbot, and Check Availability.
2. Connect **Google Drive**, **Google Calendar**, **Google Sheets**, and **Gmail** credentials (OAuth2).
3. Connect a **Supabase** credential and create the knowledge base and session/message tables.
4. Connect an **OpenRouter** credential, a **Google Gemini** credential for embeddings, and a **Cohere** credential for reranking.
5. Set the Check Availability workflow as a tool inside the Booking Chatbot's AI Agent node.
6. Embed your chat widget on your site and point it at the Booking Chatbot's webhook URL.

## Screenshots

> *Add the three workflow canvas screenshots here once uploaded to the repo.*

---

### About this project

Built as part of my AI automation portfolio. I design booking and lead-qualification systems like this — and GoHighLevel implementations — for local businesses and coaches who want every inbound chat to end in a confirmed booking instead of an unanswered message.

📂 [Full Portfolio](https://canete-jayson-portfolio.lovable.app)

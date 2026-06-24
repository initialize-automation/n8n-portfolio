# 🧑‍💼 Supervisor Agent — Multi-Agent AI Orchestration in n8n

One AI agent that delegates to three specialists — email, calendar, and research — and replies with a single unified answer, no matter which backend handled the task.

## Overview

The Supervisor Agent is the central controller in a multi-agent n8n workflow. It receives a request via Telegram (voice or text), decides which specialized agent should handle it, and routes the task accordingly. Each sub-agent works in its own domain and reports back to the Supervisor, which merges the results into one response for the user.

## The Problem

Most "AI agent" demos handle one task in isolation — send an email, check a calendar, or search the web. A real assistant needs to triage incoming requests and route them to the right tool, without the user needing to know or care which backend handled it.

## The Solution

A Supervisor Agent built in n8n that orchestrates three sub-agents and a Google Sheets data layer:

### 🧠 Supervisor Agent
- Interprets voice and text messages.
- Decides which sub-agent should handle the request.
- Combines and summarizes the sub-agent results into one response.

<img width="2031" height="492" alt="Supervisor Agent routing logic in n8n" src="https://github.com/user-attachments/assets/6f1d60c5-77a1-46f1-b351-8149bc1aa1da" />

### 📅 Calendar Agent
- Creates calendar events.
- Retrieves existing events.

<img width="2007" height="748" alt="Calendar Agent sub-workflow in n8n" src="https://github.com/user-attachments/assets/7af1c054-ce85-45cb-bed7-56a59f8c4c71" />

### 📧 Email Agent
- Sends emails on request.
- Uses Google Sheets as a lookup table for email-related metadata.

<img width="1642" height="765" alt="Email Agent sub-workflow in n8n" src="https://github.com/user-attachments/assets/afcf3982-5d11-4c76-9d7d-0ba81763ce12" />

### 🔍 Research Agent
- Runs web searches via SerpAPI and Wikipedia.
- Returns summarized, structured results instead of raw search output.

<img width="1188" height="750" alt="image" src="https://github.com/user-attachments/assets/f9e81f57-91ec-484f-a508-efa94b0adab2" />


## The Result

- One entry point (Telegram) handles email, calendar, and research requests — the user never picks a "mode."
- Each agent stays narrow and easy to debug, while the Supervisor keeps the experience unified.
- New domains (e.g. a CRM agent) can be added without touching the existing agents — the Supervisor just learns a new routing rule.

## Tech Stack

| Tool | Role |
|---|---|
| **n8n** | Workflow orchestration |
| **AI Agent (LLM)** | Task interpretation, routing, and decision-making |
| **Google Sheets** | Data storage and lookup |
| **Google Gmail** | Sending emails |
| **Google Calendar** | Creating and retrieving events |
| **SerpAPI + Wikipedia** | Web search and research |
| **Telegram** | User-facing interface |

## Setup

1. Import the workflow JSON into your n8n instance.
2. Connect **Telegram Bot**, **Gmail**, **Google Calendar**, and **Google Sheets** credentials (OAuth2).
3. Add a **SerpAPI** key for the Research Agent.
4. Connect your LLM credential to the Supervisor and sub-agent nodes.
5. Activate the workflow and message your Telegram bot to test routing.

---

## Screenshots

> <img width="2077" height="925" alt="Supervisor Agent workflow overview in n8n" src="https://github.com/user-attachments/assets/3cc45a13-1dda-475d-86c1-3eb2ed6dca54" />

### About this project

Built as part of my AI automation portfolio. I design multi-agent systems like this — and GoHighLevel implementations — for businesses that want one assistant handling multiple workflows instead of juggling separate tools.

📂 [Full Portfolio](https://canete-jayson-portfolio.lovable.app)

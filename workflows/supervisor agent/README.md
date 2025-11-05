# 🧑‍💼 Supervisor Agent

## 📖 Overview
The Supervisor Agent is an AI-powered workflow built in n8n that coordinates three specialized sub-agents. Email Agent, Calendar Agent, and Research Agent along with a Google Sheets database for retrieving structured data.

The Supervisor Agent acts as the central controller: it receives user prompts (via Telegram or other interfaces), analyzes the request, and dynamically routes tasks to the appropriate supporting agent. Each agent handles a specific domain and returns results back to the Supervisor Agent, which then sends a unified response to the user.

<img width="2077" height="925" alt="image" src="https://github.com/user-attachments/assets/3cc45a13-1dda-475d-86c1-3eb2ed6dca54" />

---
## ⚙️ Workflow  
The system consists of four main components:

🧠 Supervisor Agent
- Interprets messages, images, voice, and text.
- Determines which supporting agent to call.
- Combines and summarize results and sends the final response back to the user.

<img width="2031" height="492" alt="image" src="https://github.com/user-attachments/assets/6f1d60c5-77a1-46f1-b351-8149bc1aa1da" />

📅 Calendar Agent
- Creates events
- Retrieves events
- "Future Update : Updates or deletes calendar items "

<img width="2007" height="748" alt="image" src="https://github.com/user-attachments/assets/7af1c054-ce85-45cb-bed7-56a59f8c4c71" />

📧 Email Agent
- Sends emails
- Uses Google Sheets as a database for email-related metadata

<img width="1642" height="765" alt="image" src="https://github.com/user-attachments/assets/afcf3982-5d11-4c76-9d7d-0ba81763ce12" />

🔍 Research Agent
- Performs web searches
- Uses Wikipedia and SerpAPI to gather information
- Returns summarized and structured results
  
<img width="1208" height="675" alt="image" src="https://github.com/user-attachments/assets/adc3ecd0-7ab5-4804-907d-17e7f433b86d" />

---
## 🛠 Tools  
- **n8n** → Workflow orchestration  
- **Google Sheets** → Data storage
- **SerpApi and Wikipedia** → Web Search
- **Google Gmail** → Sending emails
- **Google Calendar** → Create and retrieves events
- **AI Agent** → Task processing and intelligent decision-making

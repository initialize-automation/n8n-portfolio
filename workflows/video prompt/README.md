# 🎥 Video Prompt Creator

## 📖 Overview
The **Video Prompt Creator** workflow runs daily to generate **unique video prompt ideas**. It checks Google Sheets to avoid repeating previous prompts, saves the new idea, and then generates a **video URL** for easy access and tracking.
<img width="1912" height="796" alt="image" src="https://github.com/user-attachments/assets/aa0f76c7-a402-45f1-8912-b2e0b44dba41" />

---
## ⚙️ Workflow  
- Scheduled to run **once per day**.  
- Reads data from **Google Sheets** to avoid duplicate ideas.  
- The **AI Agent** creates a new prompt idea.  
- New prompt is saved back into **Google Sheets**.  
- A **video URL** is generated and logged for use.  
<img width="1912" height="796" alt="image" src="https://github.com/user-attachments/assets/aa0f76c7-a402-45f1-8912-b2e0b44dba41" />

---
## 🛠 Tools  
- **n8n** → Workflow orchestration  
- **Google Sheets** → Data storage and duplication check  
- **AI Agent** → Prompt generation and video URL creation  

# 📊 Gmail Classifier 

## 📖 Overview  
The **Gmail Classifier** workflow automatically scans your inbox every minute and classifies emails based on custom rules or AI-powered descriptions. For example, all emails related to **n8n** can be automatically labeled as **N8N** for easier organization. 

<img width="2048" height="816" alt="image" src="https://github.com/user-attachments/assets/328ed315-8afb-4ee1-8072-4df35d1d0b94" />

## ⚙️ Workflow  

- A **Gmail Trigger** checks for new messages every minute.  
- Emails are sent to **Gemini AI**, which classifies them according to your defined categories or prompts.  
- Classified emails are then organized in Gmail using **labels** (e.g., “N8N”, “Work”, “Personal”).

<img width="2048" height="816" alt="image" src="https://github.com/user-attachments/assets/328ed315-8afb-4ee1-8072-4df35d1d0b94" />

---

## 🛠 Tools
- **Gemini AI** → Chat model, information extractor, text classifier  
- **Gmail** → Email source and labeling system  
- **n8n** → Workflow orchestration and automation   

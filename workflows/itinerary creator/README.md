# 🗺️ Itinerary Creator

## 📖 Overview  
The **Itinerary Creator** workflow lets you send a request via **Telegram** to automatically generate a travel itinerary for any location. The AI can **search the web**, **find relevant pictures**, and even **email the complete itinerary** to you. A quick summary is also sent back to your Telegram chat for instant feedback.  

<img width="2058" height="772" alt="Itinerary Creator Demo" src="https://github.com/user-attachments/assets/6275523e-7000-486b-a25f-c08367a1e578" />

---

## ⚙️ Workflow  
1. User sends a message request via **Telegram Bot**.  (Contains your desire location, email, how many days. e.g. "create a zambales trip for 5D4N with pictures and send in to *****@gmail.com")
2. Request is passed to an **AI Agent**.  
3. AI uses **Tavily** to search the web for location details.  
4. **Pexels API** fetches relevant pictures.  
5. A complete itinerary is compiled and sent via **Gmail**.  
6. A summary is sent back to the **Telegram Bot** for quick access.  

<img width="2058" height="772" alt="Workflow Screenshot" src="https://github.com/user-attachments/assets/6275523e-7000-486b-a25f-c08367a1e578" />

---

## 🛠 Tools & Technologies  
- **Gemini AI** → Itinerary creation and summarization  
- **Telegram Bot** → User interaction and input handling  
- **Tavily API** → Web search for itinerary details  
- **Pexels API** → Fetch relevant images  
- **Gmail** → Email delivery of the full itinerary  
- **n8n** → Workflow orchestration and automation  

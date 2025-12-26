# HackTrack 🚀

**Automated Hackathon & Tech Event Alerts using n8n + SerpAPI**

HackTrack is an automation workflow built with **n8n** that periodically checks the web for **new hackathons and tech events in India** and sends notifications when relevant events are found.

The project follows **industry-standard secret management** and is safe to publish on GitHub.

---

## ✨ Features

* 🔁 Scheduled execution (daily / weekly)
* 🔍 Fetches hackathon & tech event links via Google Search (SerpAPI)
* 🎯 Filters only relevant platforms:

  * Devfolio
  * Unstop
  * MLH
* 🚫 Removes generic listing pages
* 📭 Sends clean notifications (Telegram / Email)
* 🔐 No API keys committed to the repository

---

## 🧠 Architecture Overview

```
Schedule Trigger
→ HTTP Request (SerpAPI)
→ Split Out Items
→ IF (domain filtering)
→ Formatter
→ Notification (Telegram / Email)
```

AI is **optional** and used only for formatting (not scraping or logic).

---

## 🛠️ Tech Stack

* **n8n** – workflow automation
* **SerpAPI** – Google search results
* **Google Search** – data source
* **Telegram / Email** – notifications
* **Node.js environment variables** – secret management

---

## 📁 Project Structure

```
.
├── hacktrack.json   # Exported n8n workflow (no secrets)
├── .env             # Environment variables (NOT committed)
├── README.md
└── .gitignore
```

---

## 🔐 Environment Variables

This project requires a SerpAPI key.

Create a `.env` file in the n8n root directory:

```env
SERPAPI_KEY=your_serpapi_key_here
```

⚠️ **Do not commit `.env` to GitHub.**

Make sure `.env` is listed in `.gitignore`.

---

## 🔧 HTTP Request Configuration

In the n8n **HTTP Request** node:

```text
https://serpapi.com/search.json?engine=google&q=hackathon+India+site:devfolio.co+OR+site:unstop.com+OR+site:mlh.io&hl=en&gl=in&api_key={{ $env.SERPAPI_KEY }}
```

n8n resolves the API key at **runtime**, not from the workflow file.

---

## ▶️ How to Run

1. Clone the repository
2. Import `hacktrack.json` into n8n
3. Create a `.env` file with your SerpAPI key
4. Restart n8n
5. Activate the workflow

---

## ✅ Expected Output

If new events are found:

```
New Hackathons & Tech Events:

- Central India Hackathon 3.0
  https://unstop.com/...

- AI Builders Hackathon
  https://devfolio.co/...
```

If no new events are available:

```
No new hackathons today.
```

This is **expected behavior**, not an error.

---

## 🔒 Security Notes

* API keys are **never hardcoded**
* Workflow JSON contains **no secrets**
* Safe to share and fork
* Follows best practices for automation projects

---

## 📌 Why This Project?

Hackathons and tech events don’t update daily like job listings.
This workflow focuses on **high-signal opportunities** that update frequently and are highly valuable for students and developers.

---

## 📄 License

MIT License (or add one if you prefer)

---

## 🙌 Acknowledgements

* n8n community
* SerpAPI
* Devfolio, Unstop, MLH (event platforms)

---




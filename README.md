# 🤖 Roggy – Modular Telegram AI Gateway

![n8n](https://img.shields.io/badge/Orchestration-n8n-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white)
![OpenRouter](https://img.shields.io/badge/LLM-OpenRouter-6566F1?style=for-the-badge)
![Tavily](https://img.shields.io/badge/Search-Tavily%20AI-00D2FF?style=for-the-badge)
![Telegram](https://img.shields.io/badge/Platform-Telegram%20Bot%20API-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)

**Roggy** is a high-performance, multi-branch Telegram bot gateway built using **n8n**. Designed with a modular architecture, it intelligently routes incoming user messages through specialized paths for deterministic math evaluation, real-time web retrieval, and conversational AI—ensuring fast execution, low token usage, and strict output formatting.

---



---

## 🏛 Architecture & Workflow

```text
                  ┌──────────────────────────────┐
                  │   Telegram Trigger Node      │
                  └──────────────┬───────────────┘
                                 │
                                 ▼
                  ┌──────────────────────────────┐
                  │    Router / Classifier       │
                  └──────────────┬───────────────┘
                                 │
         ┌───────────────────────┼───────────────────────┐
         ▼                       ▼                       ▼
┌──────────────────┐   ┌──────────────────┐    ┌──────────────────┐
│  Math Switch     │   │  Tavily Search   │    │  Direct Chat     │
│  (JS Evaluation) │   │  (Web Context)   │    │  (OpenRouter)    │
└────────┬─────────┘   └────────┬─────────┘    └────────┬─────────┘
         │                      │                       │
         └──────────────────────┼───────────────────────┘
                                 │
                                 ▼
                  ┌──────────────────────────────┐
                  │  Telegram HTML Sanitizer     │
                  │  (JavaScript Node)           │
                  └──────────────┬───────────────┘
                                 │
                                 ▼
                  ┌──────────────────────────────┐
                  │    Send Telegram Message     │
                  └──────────────────────────────┘


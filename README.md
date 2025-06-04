# 🔁 Flowbit-Orchestrator: LangFlow-Powered Workflow Automation

> Real-time AI workflow orchestration using [LangFlow](https://github.com/logspace-ai/langflow) + Flowbit frontend with support for manual, webhook, and cron triggers.

---

## 🚀 Features

✅ Rebuild & execute LangFlow agents dynamically  
✅ Sync `.json` flows without server restart  
✅ Manual, Webhook, and Cron-based trigger support  
✅ Real-time logs streamed via Server-Sent Events (SSE)  
✅ Dockerized setup with LangFlow + Redis  
✅ Fully extendable workflow API  
✅ Clean UI with Next.js, Tailwind, shadcn/ui

---

## 📂 Project Structure

```
flowbit-orchestrator/
├── flows/                         # All LangFlow workflows (*.json)
├── docker-compose.yml            # LangFlow + Redis setup
├── app/                          # Next.js application
│   ├── api/                      # API Routes
│   │   ├── executions/           # Tracks and streams LangFlow runs
│   │   ├── trigger/              # Trigger workflows manually, via webhook, or cron
│   │   ├── hooks/[workflowId]/   # Public webhook triggers
│   │   └── langflow/workflows/   # Auto-detect saved LangFlow flows
├── components/                   # React components
└── lib/cron.ts                   # Cron scheduler using node-cron
```

---

## 🛠️ Setup Instructions

### 1. Start LangFlow + Redis
```bash
docker-compose up
```

LangFlow UI: [http://localhost:7860](http://localhost:7860)

### 2. Run Flowbit Frontend
```bash
pnpm install
pnpm dev
# or
npm install
npm run dev
```

Flowbit UI: [http://localhost:3000](http://localhost:3000)

---

## ⚙️ Supported Workflow Types

| Type     | Description                                       |
|----------|---------------------------------------------------|
| Manual   | Trigger from UI with text or JSON payload input   |
| Webhook  | Trigger from any external source via `/api/hooks/:workflowId` |
| Cron     | Use `lib/cron.ts` to schedule timed runs          |

---

## 🧠 Agent Templates

### Email Agent
- Prompt: `Classify the intent of this email: {email_text}`

### PDF Agent
- Prompt: `Summarize the following PDF content: {text}`

### JSON Agent
- Prompt: `Extract key fields from JSON: {json_input}`

### Classifier Agent
- Prompt: `What is the intent of this message: {text}`

---

## 📡 API Examples

**Trigger Workflow:**
```bash
POST /api/trigger
{
  "workflow": "JSON Agent",
  "input": {
    "json_input": "{"name": "Alice"}"
  }
}
```

**Webhook:**
```bash
GET /api/hooks/pdf-agent
```

---

## 📜 License

MIT License © 2025

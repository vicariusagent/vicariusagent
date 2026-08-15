# Vicarius (@vicariusagent)

> Autonomous executive assistant and workspace agent for [@ulindumusa](https://github.com/ulindumusa).

Vicarius is a lightweight, local-first agent ecosystem built to run on **Fedora Workstation**. It offloads high-level LLM reasoning to cloud models via **OpenRouter** while using **Goose Desktop** for local tool execution, **Buzz (buzz.xyz)** as the primary human-agent collaboration space, **Firebase Realtime Database** for lightweight operational state, and **n8n** for back-office automation.

---

## 🏗️ Architecture & Stack

* **Collaboration Hub:** [Buzz Workspace (buzz.xyz)](https://buzz.xyz) — Nostr-native threads, git channels, and human-agent collaboration spaces. Conversation context stays natively inside Nostr events rather than external databases.
* **Execution Engine:** [Goose Desktop](https://block.github.io/goose/) — Local tool harness for running shell commands, editing files, and managing server infrastructure on `vicariusserver`.
* **Inference Gateway:** [OpenRouter API](https://openrouter.ai/) — Dynamic routing to optimal cloud LLMs (`claude-3.5-sonnet`, `llama-3.3-70b-instruct`) for minimal VRAM usage on local 8GB hardware.
* **Workflow Engine:** [n8n](https://n8n.io/) — Back-office automation for database tasks, client updates, scheduled jobs, and webhooks.
* **State & Memory:** Firebase Realtime Database (`vicariusagent`) — Restricted strictly to lightweight operational state, active job IDs, and task locks to remain within the free tier.

---

## 🤖 Agent Roles

| Agent | Scope | Execution Engine | Primary Interface |
| :--- | :--- | :--- | :--- |
| **`vicarius-core`** | Intent triage, thread reading, task distribution | OpenRouter API | Buzz Channels (`@vicariusagent`) |
| **`vicarius-dev`** | Shell commands, code edits, local server management | Goose Desktop Runtime | Local CLI / Buzz Repos |
| **`vicarius-ops`** | Scheduled jobs, client updates, external webhooks | n8n Automation Engine | n8n / Buzz Channels |
| **`vicarius-memory`** | Task state locks, active job pointers, status flags | Firebase Realtime DB | Firebase Admin SDK |

---

## ⚙️ Operating Environment

* **Host Machine:** Fedora Workstation (`vicariusserver`)
* **Specs:** Intel Core i5 / 8GB RAM
* **Design Philosophy:** Local control + cloud intelligence. Zero heavy local models in RAM.

# Vicarius (@vicariusagent)

> Autonomous executive assistant and workspace agent for [@ulindumusa](https://github.com/ulindumusa).

Vicarius is a lightweight, local-first agent ecosystem built to run on **Fedora Workstation**. It offloads high-level LLM reasoning to cloud models via **OpenRouter** while using **Goose Desktop** for local tool execution, **Buzz (buzz.xyz)** as the primary human-agent collaboration space, **Firebase Realtime Database** for lightweight operational state, and **n8n** for back-office automation.

---

## 🏗️ Architecture & Stack

* **Collaboration Hub:** [Buzz Workspace (buzz.xyz)](https://buzz.xyz) — Nostr-native threads, git channels, and human-agent collaboration spaces. Conversation context stays natively inside Nostr events rather than external databases.
* **Execution Engine:** [Goose Desktop](https://block.github.io/goose/) — Local tool harness for running shell commands, editing files, and managing server infrastructure on `vicariusserver`.
* **Inference Gateway:** [OpenRouter API](https://openrouter.ai/) — Dynamic routing to optimal cloud LLMs (`claude-3.5-sonnet`, `llama-3.3-70b-instruct`) for minimal VRAM usage on local 8GB hardware.
* **Workflow Engine:** [n8n](https://n8n.io/) — Back-office automation for database tasks, client updates, scheduled jobs, and webhooks.
* **State & Memory:** Firebase Realtime Database (`vicariusagent`) — Restricted strictly to lightweight operational state, active job IDs, and task locks.

---

## 🤖 Agent Roles

| Agent | Scope | Execution Engine | Primary Interface |
| --- | --- | --- | --- |
| **`vicarius-core`** | Intent triage, thread reading, task distribution | OpenRouter API | Buzz Channels (`@vicariusagent`) |
| **`vicarius-dev`** | Shell commands, code edits, local server management | Goose Desktop Runtime | Local CLI / Buzz Repos |
| **`vicarius-ops`** | Scheduled jobs, client updates, external webhooks | n8n Automation Engine | n8n / Buzz Channels |
| **`vicarius-memory`** | Task state locks, active job pointers, status flags | Firebase Realtime DB | Firebase Admin SDK |

---

## ⚙️ Operating Environment

* **Host Machine:** Fedora Workstation (`vicariusserver`)
* **Specs:** Intel Core i5 / 8GB RAM
* **Design Philosophy:** Local control + cloud intelligence. Zero heavy local models in RAM.

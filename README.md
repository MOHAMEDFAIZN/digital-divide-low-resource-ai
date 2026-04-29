# 🌐 Offline AI Chatbot — Low-Resource AI for Everyone

<div align="center">

![Banner](https://img.shields.io/badge/Bridging%20the%20AI%20Intelligence%20Gap-Offline%20%7C%20Private%20%7C%20Free-4A90D9?style=for-the-badge&labelColor=1a1a2e)

[![React](https://img.shields.io/badge/React-19.0-61DAFB?logo=react&logoColor=white&style=flat-square)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?logo=typescript&logoColor=white&style=flat-square)](https://www.typescriptlang.org/)
[![Ollama](https://img.shields.io/badge/Ollama-Local%20AI-white?logo=ollama&style=flat-square)](https://ollama.com/)
[![WebLLM](https://img.shields.io/badge/WebLLM-Browser%20AI-orange?style=flat-square)](https://webllm.mlc.ai/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](./LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen?style=flat-square)](https://github.com/)
[![Vitest](https://img.shields.io/badge/Tested%20with-Vitest-6E9F18?logo=vitest&logoColor=white&style=flat-square)](https://vitest.dev/)

**A fully offline AI chatbot platform built to close the Digital Divide — running powerful language models locally on any device, with zero internet dependency.**

[🚀 Quick Start](#installation-guide) · [📖 How It Works](#workflow--how-it-works) · [🛠️ Tech Stack](#tech-stack) · [🗺️ Roadmap](#future-enhancements)

</div>

---

## 🎯 Project Overview

**Offline AI Chatbot** is a full-stack AI chat application that enables students, educators, and users in low-resource environments to interact with large language models **entirely offline** — no cloud subscription, no high-speed internet, no data privacy concerns.

It supports **two AI inference modes**:
- **Ollama** — runs local LLMs natively on device through a backend Express server
- **WebLLM** — executes AI models directly in the browser using WebGPU, with no server required

Built as part of the **"Digital Divide 2.0: Low-Resource AI"** academic initiative by **Team Dev Vengers**, this platform addresses a critical equity gap: most AI tools today require high-end hardware and reliable internet — leaving behind rural students, low-income learners, and schools in under-served communities.

---

## ❗ Problem Statement

The modern AI revolution is creating a new kind of inequality — the **AI Intelligence Gap**:

- 🌐 Most AI tools require **high-speed internet** and **cloud-based processing**
- 💻 Leading AI platforms demand **high-end hardware** that most students cannot afford
- 🏫 Schools in rural or low-income areas are systematically **excluded from AI-powered education**
- 🔒 Cloud AI tools raise **privacy concerns** about student data sent to third-party servers

While AI-enabled students surge ahead, millions of learners are left behind — not because of lack of intelligence, but because of lack of access.

---

## ✅ Proposed Solution

An open-source, **fully offline AI chatbot platform** that:

- Runs **state-of-the-art LLMs locally** on the user's own device
- Works in **zero-internet environments** — no Wi-Fi, no data plan needed
- Supports **vision-capable models** (LLaVA, BakLLaVA) for multimodal input
- Parses and processes **PDFs, images, code files, and text documents** as chat attachments
- Provides a **modern, accessible UI** with dark/light mode, keyboard shortcuts, and mobile responsiveness
- Keeps all data **100% private** — nothing ever leaves the device

---

## ✨ Key Features

- **🔌 Dual AI Backend** — Switch seamlessly between Ollama (local server) and WebLLM (in-browser inference)
- **📁 Rich File Attachments** — Upload and chat with PDFs, images, code files, CSVs, JSON, YAML, Markdown, and 20+ programming languages (up to 50MB)
- **👁️ Vision Model Support** — Automatically detects and enables image input for vision-capable models (LLaVA, BakLLaVA)
- **🔄 Real-Time Streaming** — Token-by-token streaming responses with abort/cancel support
- **🧠 Conversation Memory** — Full multi-turn context with token counting and context window management
- **⚙️ Model Settings** — Configurable temperature, top-p, seed, and system message per session
- **🌙 Dark / Light Mode** — Persistent theme preference via localStorage
- **⌨️ Keyboard Shortcuts** — Power-user hotkeys for common actions
- **📱 Responsive Design** — Mobile-first layout using React Responsive
- **🔍 Model Selector** — Browse and switch between all locally available Ollama and WebLLM models
- **✅ Comprehensive Tests** — Unit and integration tests via Vitest + React Testing Library
- **🔒 Privacy by Design** — Zero telemetry, zero cloud, zero data leakage

---

## 🛠️ Tech Stack

### Frontend

| Technology | Purpose |
|---|---|
| React 19 | UI Framework |
| TypeScript 5 | Type-safe development |
| Vite 5 | Build tool & dev server |
| Tailwind CSS v4 | Utility-first styling |
| shadcn/ui + Radix UI | Accessible UI components |
| Framer Motion | Smooth animations |
| React Router DOM v6 | Client-side routing |
| react-markdown + remark-gfm | Markdown rendering |
| react-syntax-highlighter | Code block highlighting |
| Sonner | Toast notifications |
| pdfjs-dist | In-browser PDF text extraction |
| js-tiktoken | Token counting |

### AI & Backend

| Technology | Purpose |
|---|---|
| Ollama | Local LLM inference server |
| @mlc-ai/web-llm | Browser-based LLM execution (WebGPU) |
| Express.js | Backend REST API server |
| ollama (npm client) | Node.js Ollama API client |
| TypeScript (tsx/nodemon) | Backend runtime |

### Dev & Testing

| Technology | Purpose |
|---|---|
| Vitest | Unit & integration testing |
| React Testing Library | Component & hook testing |
| ESLint | Code quality enforcement |
| concurrently | Run frontend + backend simultaneously |

---

## 🤖 AI/ML Concepts Used

- **Local LLM Inference** — Running quantized language models (GGUF format via Ollama) on consumer hardware without GPU requirements
- **In-Browser AI (WebLLM)** — Executing transformer models directly in Chromium browsers using WebGPU via Apache TVM compiler stack
- **Streaming Token Generation** — Chunked HTTP streaming (`Transfer-Encoding: chunked`) for real-time token delivery from Ollama; `ReadableStream<Uint8Array>` for WebLLM
- **Context Window Management** — Token counting via `js-tiktoken` to validate conversation history against model-specific context limits (2048 tokens for WebLLM, model-dependent for Ollama)
- **Multimodal Input** — Image-to-base64 encoding pipeline for vision-capable models; heuristic detection of vision support based on model name and family
- **Model Quantization Awareness** — UI surfaces quantization level (q4, q8) and parameter size (1B, 3B, 7B) extracted from model metadata
- **System Prompt Engineering** — Configurable system messages injected at conversation start to guide model behavior
- **PDF Text Extraction** — Multi-page PDF parsing via pdf.js for document-aware AI conversations

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    React Frontend (Vite)                 │
│                                                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │  ChatContext │  │ ModelContext │  │AttachContext │  │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  │
│         │                 │                 │           │
│  ┌──────▼─────────────────▼─────────────────▼───────┐  │
│  │              OfflineChatbot Component             │  │
│  │   ChatSidebar │ ChatNavbar │ ChatMainContent       │  │
│  └─────────────────────────┬─────────────────────────┘  │
│                             │                           │
│           ┌─────────────────┼──────────────┐            │
│           ▼                                ▼            │
│  ┌──────────────────┐            ┌──────────────────┐  │
│  │  provider.service│            │  model.service   │  │
│  │  (Ollama / WebLLM│            │  (list models)   │  │
│  │   routing logic) │            └──────────────────┘  │
│  └─────────┬────────┘                                   │
└────────────┼───────────────────────────────────────────┘
             │
     ┌───────┴──────────┐
     │                  │
     ▼                  ▼
┌─────────────┐   ┌──────────────────────────────┐
│  Express.js │   │   WebLLM Engine (Browser)    │
│  Backend    │   │   @mlc-ai/web-llm             │
│  /ask POST  │   │   WebGPU inference           │
│  /models GET│   │   ReadableStream output      │
└──────┬──────┘   └──────────────────────────────┘
       │
       ▼
┌──────────────┐
│   Ollama     │
│  Local Server│
│  (port 11434)│
│  GGUF Models │
└──────────────┘
```

---

## 🔄 Workflow / How It Works

**Step 1 — Model Selection**
The user opens the model selector and chooses from locally installed Ollama models or WebLLM browser models. Vision support is auto-detected from model metadata.

**Step 2 — Attachment (Optional)**
Files are uploaded via drag-and-drop or the file picker. The app routes each file type to the appropriate parser: `parseTextFile`, `parseImageFile` (base64), or `parsePDFFile` (pdf.js multi-page extraction). Files up to 50MB are supported.

**Step 3 — Message Submission**
The user types a prompt. The `ChatContext` assembles the full conversation history, system message, prompt, and any file attachments. Token count is validated against the model's context window before submission.

**Step 4 — AI Inference (Streaming)**
- **Ollama path**: The Express backend receives a POST `/ask` request and calls `ollama.chat()` with `stream: true`. Chunks are forwarded to the frontend via chunked HTTP transfer.
- **WebLLM path**: The `WebLLMManager` in the browser calls `createCompletion()` via WebGPU. A `ReadableStream` delivers token deltas using `requestAnimationFrame` batching for smooth UI updates.

**Step 5 — Response Rendering**
The `useStreamingResponse` hook accumulates token chunks in real-time. The `ChatMessage` component renders the growing response with full Markdown support (tables, code blocks with syntax highlighting, GFM).

**Step 6 — Conversation Continues**
The completed response is appended to the conversation history. The user can continue chatting, adjust model parameters in Settings, or start a new chat from the sidebar.

---

## 📦 Installation Guide

### Prerequisites

| Requirement | Version |
|---|---|
| Node.js | ≥ 18.x |
| npm | ≥ 9.x |
| Ollama (for local models) | Latest |

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/offline-ai-chatbot.git
cd offline-ai-chatbot
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment

Copy the example environment file and set your API port:

```bash
cp .env.example .env
```

Default `.env`:
```env
VITE_API_PORT=5001
```

### 4. Install Ollama & Pull a Model

Download Ollama from [ollama.com](https://ollama.com) and pull a model:

```bash
# Lightweight model (recommended for low-resource devices)
ollama pull llama3.2:1b

# Mid-range model
ollama pull llama3.2:3b

# Vision-capable model
ollama pull llava:7b
```

---

## ▶️ How to Run Locally

### Start Full Stack (Frontend + Backend)

```bash
npm run start
```

This runs both the Vite dev server and the Express backend concurrently (with automatic port cleanup).

### Run Frontend Only

```bash
npm run dev
```

### Run Backend Only

```bash
npm run server
```

### Run Tests

```bash
npm run test
```

### Build for Production

```bash
npm run build
```

**Access the app at:** `http://localhost:5173`

**API server runs at:** `http://localhost:5001` (or next available port)

> **WebLLM Mode:** No backend needed. Select any WebLLM model from the model selector. The model downloads to your browser on first use and runs entirely client-side via WebGPU.

---

## 📁 Folder Structure

```
offline-chatbot-main/
│
├── server/                          # Express.js Backend
│   ├── index.ts                     # Server entry point, port management
│   ├── startup.js                   # Port cleanup utility
│   ├── routes/
│   │   ├── chat.routes.ts           # POST /ask — Ollama streaming endpoint
│   │   └── model.routes.ts          # GET /models — list available models
│   ├── types/
│   │   └── chat.types.ts            # Backend request/response types
│   └── utils/
│       ├── logger.ts                # Colored console logger
│       └── port-manager.ts          # Auto port conflict resolution
│
├── src/                             # React Frontend
│   ├── App.tsx                      # Root component
│   ├── main.tsx                     # React DOM entry
│   ├── components/
│   │   ├── offline-chatbot/         # Core chatbot feature module
│   │   │   ├── OfflineChatbot.tsx   # Root chatbot component
│   │   │   ├── components/
│   │   │   │   ├── attachments/     # File upload & preview components
│   │   │   │   ├── chat/            # ChatMessage, ChatInput, ChatContainer
│   │   │   │   ├── dialogs/         # SettingsDialog (temperature, top-p, seed)
│   │   │   │   ├── layout/          # Navbar, Sidebar, MainContent
│   │   │   │   ├── model-selector/  # Ollama + WebLLM model browser
│   │   │   │   └── ui/              # Markdown renderer, scroll helpers
│   │   │   ├── config/
│   │   │   │   ├── model-configs.ts # Vision model detection heuristics
│   │   │   │   └── attachments.config.ts # Supported file types & MIME types
│   │   │   ├── contexts/            # React context providers
│   │   │   │   ├── ApplicationContext.tsx
│   │   │   │   ├── AttachmentContext.tsx
│   │   │   │   ├── ChatContext.tsx  # Message history, streaming state
│   │   │   │   └── ModelContext.tsx # Active model, provider selection
│   │   │   ├── hooks/
│   │   │   │   ├── useHotkeys.ts          # Keyboard shortcut bindings
│   │   │   │   ├── useLocalStorage.ts     # Persistent settings
│   │   │   │   ├── useScrollToBottom.ts   # Auto-scroll chat
│   │   │   │   └── useStreamingResponse.ts # Stream accumulator hook
│   │   │   ├── services/
│   │   │   │   ├── chat.service.ts     # Chat request orchestration
│   │   │   │   ├── message.service.ts  # Message formatting
│   │   │   │   ├── model.service.ts    # Fetch available models
│   │   │   │   ├── provider.service.ts # Ollama/WebLLM routing & inference
│   │   │   │   └── token.service.ts    # Token counting & context validation
│   │   │   ├── types/                  # TypeScript interfaces
│   │   │   └── utils/
│   │   │       ├── api.ts              # Axios API client config
│   │   │       ├── deviceUtility.ts    # Device/browser capability checks
│   │   │       ├── modelUtils.ts       # Model metadata utilities
│   │   │       └── attachment/
│   │   │           ├── conversion.ts   # File-to-API format converters
│   │   │           ├── parsers.ts      # Text/image/PDF parsers
│   │   │           └── validation.ts   # File type & size validators
│   │   └── ui/                         # shadcn/ui base components
│   ├── contexts/
│   │   └── ThemeContext.tsx            # Dark/light mode provider
│   └── styles/                         # Global CSS & Tailwind config
│
├── tests/                           # Test suite
│   ├── components/
│   │   └── ChatMessage.test.tsx
│   ├── contexts/
│   │   ├── ChatContext.test.tsx
│   │   └── ChatContextInputBlocking.test.tsx
│   ├── hooks/
│   │   ├── useHotkeys.test.ts
│   │   └── useLocalStorage.test.ts
│   └── utils/
│       ├── fileValidation.test.ts
│       └── token-service.test.ts
│
├── public/                          # Static assets & PWA icons
├── index.html                       # Vite HTML entry
├── vite.config.ts                   # Vite + PWA plugin config
├── tsconfig.json                    # Frontend TypeScript config
├── tsconfig.server.json             # Backend TypeScript config
├── package.json                     # Dependencies & scripts
└── .env                             # Environment variables
```

---

## 🖼️ Screenshots

> The following sections describe the UI panels as presented in the project demonstration.

### Main Chat Interface
The primary chat view features a collapsible sidebar for chat history, a top navbar with the model selector, and a full-width message thread with streaming Markdown rendering and syntax-highlighted code blocks.

### Model Selector
A popover panel listing all locally installed Ollama models alongside available WebLLM browser models. Each model shows its provider, parameter size, and quantization level.

### File Attachment Preview
Before sending, attached files (PDFs, images, code files) display as preview cards below the input bar, showing file name, type icon, and file size.

### Settings Dialog
A modal for configuring model parameters: system message, temperature slider, top-p, and seed — all persisted to localStorage per session.

### Dark / Light Mode
Full theme support with persistent preference, accessible across all components via React Context.

---

## 🎬 Demo

> **Live demo coming soon.**

To see the project in action locally:

1. Complete the [Installation Guide](#installation-guide)
2. Run `npm run start`
3. Open `http://localhost:5173`
4. Select an Ollama model or a WebLLM model
5. Start chatting — fully offline!

For a WebLLM-only demo (no Ollama installation needed):
1. Run `npm run dev` (frontend only)
2. Select any WebLLM model
3. Wait for the model to download to your browser on first load
4. Chat entirely in-browser with no server

---

## 🔭 Future Enhancements

- **📱 Mobile App (React Native / PWA)** — Package as a Progressive Web App for installable offline use on Android low-end devices
- **💬 SMS Gateway Integration** — Connect to SMS-capable devices for AI access on basic phones with no internet (as outlined in the project vision)
- **🗣️ Voice Input / TTS** — Speech-to-text input and text-to-speech output for accessibility
- **📚 RAG (Retrieval-Augmented Generation)** — Local vector store (e.g., ChromaDB) for document-grounded responses
- **🌍 Multi-Language UI** — Localization support for regional languages spoken in under-served communities
- **🔗 Model Fine-Tuning Interface** — Guide users to fine-tune smaller models on domain-specific educational content
- **📊 Usage Analytics (Local)** — On-device session analytics dashboard (no cloud) for educators to track usage
- **🔐 User Profiles** — Local authentication and per-user conversation history
- **🖨️ Export Conversations** — Download chat history as PDF or Markdown

---

## 📚 Learning Outcomes

Through building this project, the team gained hands-on experience in:

- Architecting a **full-stack TypeScript application** with a clean frontend/backend separation
- Integrating **local LLM inference** via the Ollama API and Node.js streaming
- Implementing **in-browser AI execution** using WebLLM and WebGPU APIs
- Building **real-time streaming UIs** with React hooks and ReadableStream
- Designing **context-aware AI conversations** with token budget management
- Handling **multimodal inputs** — parsing PDFs, images, and diverse file types for AI consumption
- Writing **production-quality tests** for React components, hooks, and utility services
- Applying **accessibility and responsive design** principles to an AI product
- Understanding **AI equity and digital inclusion** as a systems-level design constraint

---

## 👥 Team Members

**Team Dev Vengers**

| Name | Role |
|------|------|
| Team Dev Vengers | Full-Stack AI Development |

> *This project was developed as an academic initiative addressing digital equity through offline AI access.*

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](./LICENSE) file for details.

You are free to use, modify, and distribute this project for educational and non-commercial purposes.

---

## 🏷️ GitHub Topics

`offline-ai` · `local-llm` · `ollama` `webllm` · `react` · `typescript` · `digital-divide` · `education-technology` · `privacy-first-ai` · `web-llm` · `no-internet-ai` · `low-resource-ai` · `student-project`

---

## 📚 Resources & References

- [Ollama Official Website](https://ollama.com)
- [Ollama Model Library](https://ollama.com/library)
- [WebLLM Official Website](https://webllm.mlc.ai/)
- [WebLLM GitHub Repository](https://github.com/mlc-ai/web-llm)
- [MLC-AI Documentation](https://llm.mlc.ai/)

---

<div align="center">

**Built with ❤️ by Team Dev Vengers**

*Closing the AI gap — one device at a time.*

⭐ If this project helped you, please consider starring the repository!

</div>

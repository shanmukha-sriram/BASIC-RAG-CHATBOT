# 🛡️ BASIC-RAG-CHATBOT — Insurellm AI Assistant

An intelligent question-answering chatbot built for **Insurellm**, a fictional Insurance Tech company. Designed as an expert knowledge worker for Insurellm employees — it accurately answers questions about the company's **employees, products, contracts, and company background** using **Retrieval-Augmented Generation (RAG)**.

> 💡 Built for accuracy and **low cost**: lightweight keyword retrieval feeds only the relevant context to the LLM — no embeddings, no vector DB, no extra API costs.

---

## ✨ Features

- 🔍 **Keyword-Based Retrieval** — indexes the full knowledge base (employees, products, contracts, company docs) by filenames and document headings
- 🤖 **LLM-Powered Answers** — retrieved context is injected into the system prompt of an LLM accessed via OpenRouter
- 💰 **Low-Cost Design** — simple keyword matching instead of paid embedding/vector-store services
- 🎨 **Clean Chat Interface** — polished Gradio UI with chat bubbles, avatars, and a clear-conversation button
- 🙅 **Grounded & Honest** — the assistant answers only from the provided context and admits when it doesn't know, minimizing hallucinations
- 🌍 **Shareable Link** — public sharing support via ngrok

---

## 🏗️ How It Works

```
User Question
     │
     ▼
┌──────────────────────┐
│  Keyword Retrieval   │  ← question words are matched against an index of
│   (knowledge dict)   │    filenames & document headings from knowledge-base/
└──────────────────────┘
     │  relevant documents
     ▼
┌──────────────────────┐
│    LLM (OpenRouter)  │  ← system prompt = role + retrieved context
│    via OpenAI SDK    │
└──────────────────────┘
     │  answer
     ▼
 Gradio Chat UI   →   👤 User  🤖 Assistant
```

---

## 📂 Project Structure

```
BASIC-RAG-CHATBOT/
├── rag-chatbot.ipynb       # Main application code
├── requirements.txt        # Python dependencies
├── .env                    # API keys (NOT committed)
└── knowledge-base/         # Insurellm documents
    ├── company/            # Company overview, culture, careers
    ├── employees/          # HR records (role, career history, salary)
    ├── products/           # Product docs (Carllm, Bizllm, Rellm, etc.)
    └── contracts/          # Client contracts (terms, pricing, parties)
```

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/shanmukha-sriram/BASIC-RAG-CHATBOT.git
cd BASIC-RAG-CHATBOT
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Set up environment variables

Create a `.env` file in the project root:

```env
OXALPHA_APIKEY=your_openrouter_api_key_here
```

> ⚠️ **Never commit your `.env` file.** Get a free API key at [openrouter.ai/keys](https://openrouter.ai/keys).

### 4. Run the app

```bash
python rag-chatbot.ipynb
```

The chatbot opens in your browser at `http://127.0.0.1:7860`.

---

## 💬 Example Questions
![Insurellm Assistant Screenshot](<img width="1622" height="1027" alt="Screenshot 2026-08-30 175123" src="https://github.com/user-attachments/assets/79946fb7-aa32-4d3c-a382-82baedd83081" />
)


![Insurellm Assistant Screenshot](<img width="1575" height="1030" alt="Screenshot 2026-08-30 175146" src="https://github.com/user-attachments/assets/482ba042-f326-4e4c-abbd-f0b9cf117e6d" />
)

| Question | Answered from |
|---|---|
| "Who is Avery Lancaster?" | Employee HR record |
| "Who is Avery?" | Employee HR record (first-name lookup) |
| "What is Carllm and what is its pricing?" | Product document |
| "Tell me about the Advantage Medical Coverage contract" | Contract document |
| "How many employees does Insurellm have?" | Company documents |


---

## 🔑 Design Decisions

1. **Keyword retrieval over embeddings** — the knowledge base is small and well-structured (employee names & product names appear in filenames/headings), so keyword lookup is fast, accurate, and completely free.
2. **Context injection via system prompt** — only the matched documents are sent to the LLM, keeping prompts short and costs minimal.
3. **Grounded instructions** — the system prompt tells the model to answer only from the given context and say "I don't know" otherwise — critical for an accurate employee-facing assistant.

---

## 📄 License

This project is released under the MIT License.

---

⭐ If this project helped you learn RAG, consider giving it a star!

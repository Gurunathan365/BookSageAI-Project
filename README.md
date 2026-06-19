# BookSageAI

> *Ask questions about your books. Get answers that actually make sense.*

BookSageAI is a **Retrieval-Augmented Generation (RAG)** application that lets you have intelligent conversations with your book collection. Upload a book, ask anything — the AI finds the right passages and answers in context.

---

## Features

- **Upload & Index** — Drop in a book (PDF) and it's instantly searchable
- **Natural Language Q&A** — Ask questions in plain English, get grounded answers
- **Source Citations** — Responses include the exact passages they're based on
- **Fast Retrieval** — Vector-based semantic search finds relevant content quickly
- **Clean Web UI** — Minimal React interface, no clutter

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React + Vite + Tailwind CSS |
| Backend | Python (FastAPI / Flask) |
| Embeddings | (e.g. OpenAI / HuggingFace) |
| Vector Store | (e.g. FAISS / Chroma) |
| LLM | (e.g. GPT-4 / Claude) |

> Update the table above with your exact libraries if they differ.

---

## Getting Started

### Prerequisites

- Node.js ≥ 18
- Python ≥ 3.10
- An OpenAI API key (or whichever LLM provider you're using)

---

### 1. Clone the repo

```bash
git clone https://github.com/Gurunathan365/BookSageAI-Project.git
cd BookSageAI-Project
```

---

### 2. Set up the Python backend

```bash
cd py-backend
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Create a `.env` file inside `py-backend/`:

```env
OPENAI_API_KEY=your_key_here
```

Start the server:

```bash
python main.py
```

The backend runs at `http://localhost:8000` by default.

---

### 3. Set up the frontend

```bash
# from the project root
npm install
npm run dev
```

The app opens at `http://localhost:5173`.

---

## Project Structure

```
BookSageAI-Project/
├── public/               # Static assets
├── src/                  # React frontend source
│   ├── components/       # UI components
│   └── ...
├── py-backend/           # Python RAG backend
│   ├── main.py           # API entry point
│   ├── rag.py            # Retrieval + generation logic
│   └── requirements.txt
├── index.html
├── vite.config.js
└── package.json
```

---

## How It Works

```
User Question
     │
     ▼
Embed the question  ──►  Search vector store  ──►  Retrieve top-k chunks
                                                          │
                                                          ▼
                                              Feed chunks + question to LLM
                                                          │
                                                          ▼
                                                   Answer with sources
```

1. When a book is uploaded, it's split into chunks and embedded into a vector store.
2. When the user asks a question, the question is embedded and matched against stored chunks.
3. The most relevant chunks are passed to an LLM along with the question.
4. The LLM returns a grounded answer, referencing the actual book content.

---

## Configuration

| Variable | Description | Default |
|----------|-------------|---------|
| `OPENAI_API_KEY` | Your LLM API key | — |
| `CHUNK_SIZE` | Text chunk size for indexing | `500` |
| `TOP_K` | Number of chunks retrieved per query | `5` |

---

## Contributing

Contributions are welcome! Here's how:

1. Fork the repo
2. Create a branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "add your feature"`
4. Push and open a Pull Request

---

## License

This project is open source. Add a `LICENSE` file if you'd like to specify terms.

---

<p align="center">Built by <a href="https://github.com/Gurunathan365">Gurunathan365</a></p>

# RAG (Retrieval-Augmented Generation) System

A complete RAG implementation using LangChain, HuggingFace embeddings, and local LLMs for question-answering over web content.

## 🚀 Features

- **Web Content Loading**: Scrapes and processes web pages
- **Document Splitting**: Intelligent text chunking with overlap
- **Vector Database**: Chroma DB for semantic search
- **Free Embeddings**: HuggingFace sentence-transformers
- **Local LLM**: Microsoft Phi-3.5-mini-instruct (no API costs)
- **100% Free**: No API keys required for basic functionality

## 📋 Prerequisites

- Python 3.11+
- 8GB+ RAM (for local model)
- Git

## 🛠️ Installation

1. **Clone the repository**
```bash
git clone https://github.com/Rajan-sharma-0/RAG.git
cd RAG
```

2. **Install dependencies**
```bash
pip install langchain langchain_community langchainhub chromadb langchain-openai python-dotenv sentence-transformers transformers torch
```

3. **Set up API keys (optional)**
Create a `keys` file in the root directory:
```
OPENROUTER_API_KEY=your_key_here
```
*Note: API keys are only needed if using cloud-based LLMs*

## 📖 Usage

### Basic Workflow

1. **Load Environment Variables** (Cell 2)
   - Loads API keys from `keys` file

2. **Load Web Content** (Cell 3)
   - Fetches content from specified URLs
   - Example: `https://www.educosys.com/course/lld`

3. **Split Documents** (Cell 4)
   - Chunks text into 1000-character segments
   - 100-character overlap for context preservation

4. **Create Vector Store** (Cell 6)
   - Generates embeddings using HuggingFace
   - Stores in Chroma vector database

5. **Set Up Retriever** (Cell 10)
   - Configures semantic search

6. **Load LLM** (Cell 12)
   - Downloads and initializes Phi-3.5-mini model
   - First run takes 5-10 minutes (7GB download)

7. **Create RAG Chain** (Cells 11, 13-15)
   - Combines retriever + LLM + prompt

8. **Ask Questions** (Cell 16)
   - Query your documents!

### Example Query

```python
rag_chain.invoke("What is LLD?")
```

## 🏗️ Architecture

```
User Query
    ↓
Retriever (finds relevant chunks)
    ↓
Context + Question → Prompt
    ↓
LLM (generates answer)
    ↓
Final Answer
```

## 🔧 Components

| Component | Technology | Purpose |
|-----------|------------|---------|
| Web Loader | WebBaseLoader | Scrapes web content |
| Text Splitter | RecursiveCharacterTextSplitter | Chunks documents |
| Embeddings | HuggingFace (all-MiniLM-L6-v2) | Converts text to vectors |
| Vector DB | Chroma | Stores and searches embeddings |
| LLM | Phi-3.5-mini-instruct | Generates answers |
| Framework | LangChain | Orchestrates the pipeline |

## 📁 Project Structure

```
RAG/
├── 01RAG.ipynb          # Main notebook
├── keys                 # API keys (gitignored)
├── .gitignore          # Excludes sensitive files
└── README.md           # This file
```

## 🔐 Security

- `keys` and `.env` files are **gitignored**
- Never commit API keys to version control
- Use environment variables for sensitive data

## 🎯 Use Cases

- **Documentation Q&A**: Ask questions about product docs
- **Research Assistant**: Query academic papers
- **Knowledge Base**: Search company wikis
- **Learning Tool**: Understand course content

## 🐛 Troubleshooting

### "RateLimitError" with OpenRouter
- Switch to local HuggingFace model (Cell 12)
- No rate limits with local models

### "Out of Memory"
- Reduce `max_new_tokens` in pipeline
- Use a smaller model like `Phi-3-mini`

### Model Download Slow
- First run downloads ~7GB
- Subsequent runs are instant (cached)

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the MIT License.

## 👤 Author

**Rajan Sharma**
- GitHub: [@Rajan-sharma-0](https://github.com/Rajan-sharma-0)

## 🙏 Acknowledgments

- [LangChain](https://langchain.com/) - RAG framework
- [HuggingFace](https://huggingface.co/) - Models and embeddings
- [Chroma](https://www.trychroma.com/) - Vector database
- [Microsoft](https://www.microsoft.com/) - Phi-3.5 model

## 📞 Support

For questions or issues, please open an issue on GitHub.

---

⭐ Star this repo if you find it helpful!

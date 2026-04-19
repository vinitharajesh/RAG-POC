# RAG-Based Document Question Answering System

This project is a **Retrieval-Augmented Generation (RAG)** system that allows you to ask questions from your documents (.txt, .pdf, .docx) and get accurate answers using local LLMs.

---

##  Features

* 📂 Supports multiple file formats:

  * `.txt`
  * `.pdf`
  * `.docx`
*  Semantic search using embeddings
*  Local LLM inference via Ollama (no API needed)
*  Fast vector search with FAISS
*  Interactive question-answer loop

---

##  Tech Stack

* **LangChain**
* **FAISS (Vector Database)**
* **HuggingFace Embeddings**
* **Ollama (LLM)**
* **Sentence Transformers**

---

##  Installation

Install required dependencies:

```bash
pip install langchain langchain-community langchain-huggingface faiss-cpu sentence-transformers pypdf docx2txt
```

---

##  Setup Ollama

Make sure Ollama is installed and running:

```bash
ollama run tinyllama
```

(You can also use other models like `llama3`, `phi`, etc.)

---

##  Usage

## Update the file path in the script:

```python
file_path = "Nature.pdf"
```

  Ask questions:

```
 Question: What is the document about?
 Answer: ...
```

Type `exit` to quit.

---

##  How It Works

1. Load document using appropriate loader
2. Split text into chunks
3. Convert chunks into embeddings
4. Store embeddings in FAISS vector database
5. Retrieve relevant chunks based on query
6. Pass context + question to LLM
7. Generate answer

##  Example Workflow

```
User سؤال ➜ FAISS Search ➜ Context Retrieval ➜ LLM ➜ Answer
```

---

##  Example Models

* `tinyllama` (lightweight, fast)
* `phi` (better reasoning)
* `llama3` (more powerful, requires resources)

---

## ⚠️ Limitations

* Answers are limited to document context
* Performance depends on embedding quality
* Small models may give less accurate answers

---

## 📄 License

This project is open-source and free to use.

---

## &#x20;Acknowledgements

* LangChain
* HuggingFace
* Ollama
* FAISS

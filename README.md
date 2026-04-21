#  RAG-Based Document Question Answering System

A Retrieval-Augmented Generation (RAG) system that enables you to ask questions from your documents (`.txt`, `.pdf`, `.docx`) and get accurate answers using **local LLMs** — no external APIs required.

---

##  Features

*  Supports multiple file formats:

  * `.txt`
  * `.pdf`
  * `.docx`
*  Semantic search using embeddings
*  Local LLM inference via Ollama
*  Fast vector search with FAISS
*  Interactive question-answer loop
*  Fully offline (privacy-friendly)

---

##  Tech Stack

* LangChain
* FAISS (Vector Database)
* HuggingFace Embeddings
* Ollama (Local LLM runtime)
* Sentence Transformers
* Python
* Jupyter Notebook

---

##  System Requirements

* Python **3.9 or higher**
* RAM:

  * Minimum: 8GB
  * Recommended: 16GB+ (for larger models)
* OS: Windows / Linux / macOS

---

##  Installation

### 1️⃣ Install Python

Download and install Python from:
https://www.python.org/downloads/

Verify installation:

```bash
python --version
```

---

### 2️⃣ Create Virtual Environment (Recommended)

```bash
python -m venv rag_env
```

Activate it:

**Windows:**

```bash
rag_env\Scripts\activate
```

**Mac/Linux:**

```bash
source rag_env/bin/activate
```

---

### 3️⃣ Install Required Libraries

```bash
pip install langchain langchain-community langchain-huggingface faiss-cpu sentence-transformers pypdf docx2txt
```

---

### 4️⃣ Install Jupyter Notebook

```bash
pip install notebook
```

Run Jupyter:

```bash
jupyter notebook
```

---

##  Using Jupyter Notebook (Recommended)

You can run and test this project interactively using Jupyter Notebook.

###  Launch Notebook

```bash
jupyter notebook
```

* Opens in browser (`http://localhost:8888`)
* Navigate to your project folder

---

###  Create Notebook

* Click **New → Python 3**
* Rename file (e.g., `rag_demo.ipynb`)

---

### 🧪 Example Notebook Code

```python
# Import libraries
from langchain.document_loaders import PyPDFLoader
from langchain.text_splitter import CharacterTextSplitter
from langchain.vectorstores import FAISS
from langchain.embeddings import HuggingFaceEmbeddings
from langchain.llms import Ollama

# Load document
loader = PyPDFLoader("Nature.pdf")
documents = loader.load()

# Split text
text_splitter = CharacterTextSplitter(chunk_size=500, chunk_overlap=50)
texts = text_splitter.split_documents(documents)

# Create embeddings
embeddings = HuggingFaceEmbeddings()

# Store in FAISS
db = FAISS.from_documents(texts, embeddings)

# Load LLM
llm = Ollama(model="tinyllama")

# Ask question
query = "What is the document about?"
docs = db.similarity_search(query)

# Generate answer
context = " ".join([doc.page_content for doc in docs])
response = llm.invoke(f"Context: {context}\n\nQuestion: {query}")
print(response)
```

---

###  Run Cells

* Press **Shift + Enter** to run each cell
* Modify queries and test easily

---

###  Optional: JupyterLab (Better UI)

```bash
pip install jupyterlab
jupyter lab
```

---

##  Setup Ollama (Local LLM)

### Install Ollama:

https://ollama.com/download

### Run a Model:

```bash
ollama run tinyllama
```

You can also use:

* `llama3`
* `phi`
* `mistral`

---

##  Project Structure

```
rag-project/
│── main.py
│── Nature.pdf
│── README.md
│── rag_demo.ipynb
```

---

##  Usage (Python Script)

1. Update file path:

```python
file_path = "Nature.pdf"
```

2. Run script:

```bash
python RAG.ipynb
```

3. Ask questions:

```
Question: What is the document about?
Answer: ...
```

4. Exit:

```
exit
```

---

## ⚙️ How It Works

1.  Load document
2.  Split into chunks
3.  Generate embeddings
4.  Store in FAISS
5.  Retrieve relevant chunks
6.  Send to LLM
7.  Generate answer

---

## 🧠 Example Models

| Model     | Description               |
| --------- | ------------------------- |
| tinyllama | Lightweight, fast         |
| phi       | Better reasoning          |
| llama3    | Powerful (needs more RAM) |

---

##  Limitations

* Answers are limited to document context
* Performance depends on embeddings
* Small models = lower accuracy
* Large docs need tuning

---

##  Future Improvements

* Streamlit / Gradio UI
* Multi-document support
* Chat memory
* Hybrid search

---

##

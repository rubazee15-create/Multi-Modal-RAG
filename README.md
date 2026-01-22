# Multi-Modal RAG with PDFs containing Images, Tables and Text

This project implements a **Multi-Modal Retrieval-Augmented Generation (RAG)** pipeline. Unlike standard RAG that only handles text, this system uses `unstructured` to partition PDFs into text, tables and images. It then uses **Llama 3.2 Vision** (via Ollama) to generate searchable summaries of complex visual data.

### 🚀 Key Features
* **Intelligent Partitioning:** Uses `unstructured` with high-res strategy to extract atomic elements (Text, Tables, Figures).
* **Visual Understanding:** Leverages Multi-Modal LLMs to convert images and tables into rich, searchable text descriptions.
* **Chunking by Title:** Maintains document context by grouping elements under their respective headers.
* **Local Processing:** Integration with Ollama for privacy and cost-effective local inference.

### ⚙️ Project Status: Work in Progress
- [x] Document Partitioning (Unstructured)
- [x] Table & Image Extraction
- [x] AI-Enhanced Summarization (Ollama + Llama 3.2 Vision)
- [ ] Vector Store Integration (Qdrant)
- [ ] Retrieval & RAG Chain

### 🛠️ System Dependencies
Before running the code, you must install these system-level tools for document processing:

```bash
# Ubuntu/Debian
sudo apt-get install poppler-utils tesseract-ocr libmagic1

# macOS
brew install poppler tesseract libmagic

```
### ➜] Installation & Setup
#### 1. Clone the repository

```bash
git clone <repository url>

# Move in the repository folder
cd <repository name>

```
#### 2. Install the python dependencies

```bash
pip install requirements.txt

```

#### 3. Pull the Vision Model

```bash
ollama pull llama3.2-vision

```

### 🏗️ Technical Workflow
* **Partitioning**: The PDF is processed using the `unstructured` library with a `hi_res` strategy. This breaks the document into atomic elements like `NarrativeText`, `Table`, and `Image`.
* **AI Summarization**: Since standard embeddings can't "read" an image or a complex table, each mixed-media chunk is sent to **Llama 3.2 Vision**. The model analyzes the visual data and generates a detailed, searchable text description.
* **Vectorization**: These AI-generated summaries are converted into high-dimensional vectors and stored in a **Qdrant** vector database, enabling semantic search across both text and visual content.



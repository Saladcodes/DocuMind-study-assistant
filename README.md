# 📚 DocuMind -- AI-Powered Study Assistant

**DocuMind** is an AI-powered study assistant that helps students
understand academic concepts more effectively using Retrieval-Augmented
Generation (RAG).

Students can select a subject and chapter, ask questions about their
study materials, and receive AI-generated explanations grounded in the
relevant textbook content. The application combines document processing,
vector embeddings, semantic search, and conversational AI to provide a
personalized learning experience.

------------------------------------------------------------------------

## ✨ Features

-   **Subject Selection:** Choose a subject from the available Class 12
    study materials.
-   **Chapter Selection:** Select a specific chapter to focus on the
    relevant learning material.
-   **PDF Document Processing:** Extract and process content from PDF
    textbooks.
-   **Semantic Search:** Retrieve relevant information using vector
    embeddings and similarity search.
-   **AI-Powered Explanations:** Generate contextual answers using a RAG
    pipeline.
-   **Conversational Learning:** Ask follow-up questions and interact
    with the assistant like a personal tutor.
-   **Persistent Vector Storage:** Store document embeddings in ChromaDB
    for efficient retrieval.

------------------------------------------------------------------------

## 🛠️ Tech Stack

  -----------------------------------------------------------------------
  Technology                          Purpose
  ----------------------------------- -----------------------------------
  Python                              Core application development

  Streamlit                           Interactive web application

  LangChain                           RAG pipeline orchestration

  Hugging Face Sentence Transformers  Generating document and query
                                      embeddings

  ChromaDB                            Vector database and similarity
                                      search

  PyTorch                             Underlying machine learning
                                      framework

  Unstructured                        PDF document processing

  python-dotenv                       Environment variable management
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 🏗️ Architecture

DocuMind follows a Retrieval-Augmented Generation (RAG) architecture.

``` text
                USER
                  |
                  v
        Select Subject & Chapter
                  |
                  v
          Ask a Question
                  |
                  v
        Convert Question into
           Vector Embedding
                  |
                  v
          ChromaDB Retrieval
                  |
                  v
        Retrieve Relevant Text
             from PDFs
                  |
                  v
         Combine Context and
             User Question
                  |
                  v
          Language Model
                  |
                  v
          Contextual Answer
                  |
                  v
           Display in UI
```

### Document Ingestion Pipeline

Before the application can retrieve information, the source documents
must be processed.

1.  Load PDF documents from the data directory.
2.  Extract text from the documents.
3.  Split the extracted text into smaller chunks.
4.  Generate embeddings for the text chunks.
5.  Store the embeddings and associated text in ChromaDB.
6.  Retrieve relevant chunks when a user asks a question.

------------------------------------------------------------------------

## 📂 Project Structure

``` text
DocuMind-study-assistant/
│
├── data/
│   └── class_12/
│       └── biology/
│           ├── chapter_1.pdf
│           ├── chapter_2.pdf
│           └── ...
│
├── src/
│   ├── main.py
│   ├── vectorize_book.py
│   └── vectorize_script.py
│
├── vector_db/
│   └── ...
│
├── chapters_vector_db/
│   └── ...
│
├── .env
├── .gitignore
├── env_template.txt
├── requirements.txt
└── README.md
```

*Note: The directory structure above represents the main components of
the project. The exact contents of the data and vector database
directories depend on the materials processed locally.*

------------------------------------------------------------------------

## ⚙️ Installation and Setup

### 1. Clone the repository

``` bash
git clone <https://github.com/Saladcodes/DocuMind-study-assistant.git>
```

Navigate to the project directory:

``` bash
cd DocuMind-study-assistant
```

### 2. Create a virtual environment

``` bash
python -m venv .venv
```

Activate the environment on Windows PowerShell:

``` powershell
.\\.venv\\Scripts\\Activate.ps1
```

### 3. Install dependencies

``` bash
pip install -r requirements.txt
```

### 4. Configure environment variables

Create a `.env` file in the project root directory.

Use `env_template.txt` as a reference for the required environment
variables.

For example:

``` env
CLASS_SUBJECT_NAME=class_12/biology
DEVICE=cpu
```

Add any additional variables required by your language model
configuration.

**Important:** Never commit API keys, passwords, or other sensitive
credentials to GitHub.

### 5. Add study materials

Place the required PDF textbooks inside the appropriate subject
directory under `data/`.

For example:

``` text
data/
└── class_12/
    └── biology/
        ├── chapter_1.pdf
        ├── chapter_2.pdf
        └── chapter_3.pdf
```

------------------------------------------------------------------------

## 🚀 Running the Application

### Step 1: Generate the vector database

Run the document ingestion script:

``` bash
python src/vectorize_script.py
```

This processes the PDF documents, generates their embeddings, and stores
the resulting vectors in ChromaDB.

**Note:** Document ingestion can take some time, especially when
processing multiple PDFs for the first time.

The generated vector database can be reused across application sessions
as long as the underlying documents and embedding configuration remain
unchanged.

You generally do not need to rerun the ingestion script every time you
launch the application.

### Step 2: Launch the Streamlit application

``` bash
streamlit run src/main.py
```

Open the local URL displayed in the terminal to access DocuMind.

------------------------------------------------------------------------

## 🧠 How RAG Works in DocuMind

DocuMind uses Retrieval-Augmented Generation to provide answers based on
the selected study materials.

The process consists of three main stages:

**1. Retrieval**

The user's question is converted into an embedding. ChromaDB searches
the stored document embeddings to identify relevant text chunks.

**2. Augmentation**

The retrieved text is combined with the user's question to provide
relevant context to the language model.

**3. Generation**

The language model uses the question and retrieved context to generate a
contextual response.

This approach helps the assistant answer questions using the supplied
educational materials rather than relying exclusively on its general
training knowledge.

------------------------------------------------------------------------

## 🔮 Future Improvements

Potential enhancements include:

-   Support for additional subjects, classes, and educational resources.
-   Improved PDF parsing and document preprocessing.
-   Streaming responses for a more interactive user experience.
-   Source citations linking answers to textbook pages.
-   Conversation history and persistent chat sessions.
-   Cloud deployment using AWS EC2.
-   Improved error handling and logging.
-   Optimization of document ingestion and vector retrieval.

------------------------------------------------------------------------

## 👨‍💻 Author

**Deepak Kumar**

GitHub: \[https://github.com/Saladcodes]

------------------------------------------------------------------------

## 📄 License

This project is intended for educational and learning purposes.

------------------------------------------------------------------------

**A personal AI tutor designed to make studying smarter, simpler, and
more interactive.**


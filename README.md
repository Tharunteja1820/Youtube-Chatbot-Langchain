# YouTube RAG Chatbot using LangChain

A Retrieval-Augmented Generation (RAG) chatbot that allows users to ask questions about YouTube videos and receive context-aware answers based on their video transcripts.

Built using Python, LangChain, Google Gemini, and FAISS, the application extracts video transcripts, processes them into chunks, generates embeddings, and retrieves relevant information to answer user queries.

## 🚀 Features

- **YouTube Transcript Extraction:** Extract transcripts directly from YouTube videos using the YouTube Transcript API.
- **Video URL Processing:** Accept YouTube video URLs or video IDs.
- **Language Selection:** Select from the available transcript languages.
- **Text Chunking:** Split transcripts into smaller chunks using RecursiveCharacterTextSplitter.
- **Embedding Generation:** Generate vector embeddings using Google Gemini Embeddings.
- **Vector Database:** Store and retrieve transcript embeddings using FAISS.
- **Semantic Search:** Retrieve the top 3 relevant chunks based on similarity.
- **Context-Grounded Answers:** Generate answers using retrieved transcript context.
- **Multilingual Responses:** Request answers in English, Hindi, Telugu, or another specified language.
- **Conversational Memory:** Maintain conversation continuity using an automatically updated conversation summary.
- **Context-Aware Prompting:** Instruct the LLM to avoid answering questions unsupported by the transcript.

## 🏗️ Architecture

```text
             YouTube Video URL / ID
                       |
                       v
             Transcript Extraction
             (YouTube Transcript API)
                       |
                       v
               Language Selection
                       |
                       v
               Text Preprocessing
                       |
                       v
                 Text Chunking
          (RecursiveCharacterTextSplitter)
                       |
                       v
              Gemini Embeddings
                       |
                       v
                FAISS Vector Store
                       |
                       v
                  User Query
                       |
                       v
              Similarity Retrieval
                  (Top 3 Chunks)
                       |
                       v
                Prompt Augmentation
                       |
              +--------+---------+
              |                  |
              v                  v
        Retrieved Context   Conversation Summary
              |                  |
              +--------+---------+
                       |
                       v
                 Gemini LLM
                       |
                       v
              Context-Grounded Answer
                       |
                       v
             Update Conversation Summary
```

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| LangChain | RAG pipeline and orchestration |
| Google Gemini LLM | Response generation |
| Gemini Embeddings | Text embedding generation |
| FAISS | Vector storage and similarity search |
| YouTube Transcript API | Transcript extraction |
| RecursiveCharacterTextSplitter | Text chunking |
| LangChain LCEL | Building and connecting processing chains |
| python-dotenv | Environment variable management |

## ⚙️ RAG Workflow

### 1. Data Extraction

Extract video transcripts using the YouTube Transcript API. Users can provide a YouTube URL or video ID and select an available transcript language.

### 2. Text Chunking

Split the transcript into smaller chunks to improve retrieval.

- Chunk size: 1000 characters
- Chunk overlap: 200 characters

### 3. Embedding Generation

Convert text chunks into numerical vector representations using Google Gemini Embeddings (`gemini-embedding-001`).

### 4. Vector Storage

Store the generated embeddings in a FAISS vector store.

### 5. Retrieval

Use similarity-based search to retrieve the top 3 relevant transcript chunks for each user query.

### 6. Augmentation and Generation

Combine the retrieved context, user question, and conversation summary using LangChain prompt templates.

The Gemini LLM generates an answer based on the provided transcript context.

### 7. Conversational Memory

Update a concise conversation summary after each question-answer exchange to maintain conversational continuity.

## 📁 Project Structure

```text
youtube_chatbot_langchain/
│
├── youtube_chatbot_v1.ipynb
├── requirements.txt
├── .gitignore
├── .env.example
└── README.md
```

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/Youtube-Chatbot-Langchain.git
```

### 2. Navigate to the project directory

```bash
cd Youtube-Chatbot-Langchain
```

### 3. Create a virtual environment (optional)

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

### 5. Configure Google API Key

Create a `.env` file in the project root directory.

```env
GOOGLE_API_KEY=your_google_api_key
```

Obtain your API key from Google AI Studio.

Never upload your actual `.env` file to GitHub.

### 6. Run the Jupyter Notebook

```bash
jupyter notebook youtube_chatbot_v1.ipynb
```

Execute the notebook cells in order.

## 💬 Example Usage

1. Enter a YouTube video URL.
2. Select an available transcript language.
3. Wait for transcript extraction, embedding generation, and FAISS indexing.
4. Enter your question about the video.
5. Specify your preferred answer language.
6. Receive an answer based on the retrieved transcript context.
7. Continue asking questions while maintaining conversational context.

## ⚙️ Configuration

The following parameters can be adjusted in the notebook:

| Parameter | Default Value | Purpose |
|---|---|---|
| Chunk Size | 1000 | Maximum chunk size |
| Chunk Overlap | 200 | Overlap between chunks |
| Retrieval Count (k) | 3 | Number of retrieved chunks |
| Embedding Model | gemini-embedding-001 | Embedding generation |
| LLM | gemini-3.5-flash-lite | Response generation |
| Temperature | 0.2 | Controls response randomness |


## 🔮 Future Improvements

- Implement hybrid search and reranking.
- Add query rewriting and contextual retrieval.
- Introduce RAG evaluation using metrics.
- Integrate LangSmith for tracing and monitoring.
- Develop a Streamlit-based user interface.

# 🎙️ Audio-to-Insight AI

> An AI-powered application that converts audio and YouTube content into searchable knowledge through transcription, summarization, PDF export, and RAG-powered Q&A.

---

## 📌 Overview

**Audio-to-Insight AI** is a Generative AI application designed to turn long-form audio into useful, searchable information.

Users can provide:

- 🎥 YouTube URLs
- 🎵 MP3 audio files
- 🎬 MP4 video files
- 🎙️ Recorded meeting audio

The application first converts the input into audio, transcribes it using speech-to-text models, generates an AI-powered summary, and indexes the transcript for **Retrieval-Augmented Generation (RAG)**.

Users can then ask questions about the uploaded content and receive answers grounded in the original transcript.

### Core Workflow

```text
Audio / YouTube URL
        ↓
Download & Audio Processing
        ↓
Speech-to-Text Transcription
        ↓
Text Chunking
        ↓
Hugging Face Embeddings
        ↓
ChromaDB Vector Store
        ↓
RAG Retrieval
        ↓
Mistral AI LLM
        ↓
Summary / Question Answering
        ↓
PDF Export
```

---

## ❓ Problem Statement

Long meetings, lectures, interviews, podcasts, and YouTube videos often contain valuable information, but manually listening to them to find specific information is time-consuming.

Traditional solutions make it difficult to:

- Quickly understand the main points of long audio/video.
- Search for specific information inside a recording.
- Ask natural-language questions about the content.
- Convert meeting or lecture discussions into structured notes.
- Save generated summaries for later use.

This project addresses these problems by building a single AI pipeline that converts unstructured audio into **transcripts, summaries, searchable knowledge, and conversational Q&A**.

---

## 🛠️ Tools & Technologies

| Technology | Purpose |
|---|---|
| **Python** | Core application development |
| **Streamlit** | Interactive web UI |
| **OpenAI Whisper** | Speech-to-text transcription |
| **Sarvam AI** | Speech/transcription support for Indian languages |
| **Mistral AI** | LLM for summarization and question answering |
| **Hugging Face** | Local text embedding models |
| **LangChain** | RAG pipeline and LLM orchestration |
| **LCEL** | Building composable LangChain pipelines |
| **ChromaDB** | Vector database for transcript chunks |
| **yt-dlp** | Downloading audio from YouTube |
| **FFmpeg** | Audio/video conversion and preprocessing |
| **FPDF2** | Exporting summaries as PDF |

---

## ⚙️ Methods

- Audio Input & Processing
- Speech-to-Text
- Text Chunking
- Embedding Generation
- Vector Storage with ChromaDB
- RAG-Powered Q&A
- AI Summarization
- PDF Export

## 📊 Dashboard / Model / Output

### Streamlit Dashboard

The application provides a simple Streamlit interface where users can:

1. Enter a YouTube URL or upload an audio/video file.
2. Process and transcribe the input.
3. View the generated transcript.
4. Generate and read an AI summary.
5. Export the summary as a PDF.
6. Ask questions about the processed content using RAG.

### System Architecture

```text
┌─────────────────────┐
│   Audio / Video     │
│ YouTube / MP3 / MP4 │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│   yt-dlp + FFmpeg   │
│ Audio Processing    │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│ Whisper / Sarvam AI │
│   Transcription     │
└──────────┬──────────┘
           ↓
     ┌─────┴─────┐
     ↓           ↓
┌──────────┐  ┌─────────────┐
│Summary   │  │Text Splitter│
│Mistral AI│  └──────┬──────┘
└────┬─────┘         ↓
     │        ┌──────────────┐
     │        │ Hugging Face │
     │        │  Embeddings  │
     │        └──────┬───────┘
     │               ↓
     │        ┌──────────────┐
     │        │  ChromaDB    │
     │        │ Vector Store │
     │        └──────┬───────┘
     │               ↓
     │        ┌──────────────┐
     │        │ RAG Retriever│
     │        └──────┬───────┘
     │               ↓
     │        ┌──────────────┐
     └───────→│  Mistral AI  │
              │     LLM      │
              └──────┬───────┘
                     ↓
            ┌─────────────────┐
            │ Q&A / PDF Output│
            └─────────────────┘
```

---

## 🚀 How to Run This Project

### 1. Clone the Repository

```bash
git clone https://github.com/yashveersaini/VoxIntel
cd VoxIntel
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

Activate it:

**Windows**

```bash
venv\Scripts\activate
```

**Linux / macOS**

```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Install FFmpeg

FFmpeg must be installed and available in your system PATH because it is used for audio/video processing and conversion.

Verify the installation:

```bash
ffmpeg -version
```

### 5. Configure API Keys

Create a `.env` file in the project root:

```env
MISTRAL_API_KEY=your_mistral_api_key
WHISPER_MODEL=model_size
SARVAM_API_KEY=your_sarvam_api_key
SARVAM_STT_MODEL=model_name
```

> **Important:** Never commit your `.env` file or API keys to GitHub.

### 6. Run the Streamlit Application

```bash
streamlit run app.py
```

The application will open in your browser.

---

## 📈 Results & Conclusion

The project provides an end-to-end workflow for converting long-form audio and video into useful, searchable knowledge.

It combines:

**Speech-to-Text → Summarization → Embeddings → Vector Search → RAG → Q&A → PDF Export**

The result is a practical Generative AI application that can significantly reduce the time required to consume and search through long meetings, lectures, interviews, podcasts, and YouTube content.

This project also demonstrates practical experience with **LLM integration, RAG architecture, vector databases, embeddings, LangChain LCEL, audio processing, and AI application development**.

---

## 🔮 Future Work

Potential improvements include:

- 🌍 Better multilingual transcription and translation support.
- 📝 Speaker diarization to identify different speakers in meetings.
- ⏱️ Timestamp-based answers that link responses to exact parts of the recording.
- 📚 Support for multiple documents/audio files in a single knowledge base.
- 💬 Conversation memory for multi-turn Q&A.
- 🔐 User authentication and private knowledge bases.
- ☁️ Cloud storage for uploaded recordings and generated outputs.
- 📊 RAG evaluation using metrics such as faithfulness and retrieval quality.
- 🚀 Production deployment with scalable background processing.
- 📌 Source citations showing the transcript sections used to generate each answer.

---

## 👨‍💻 Author

**Yashveer**

B.Tech CSE — AI/ML  
Generative AI & Machine Learning Enthusiast

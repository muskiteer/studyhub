# 🎓 SubRevision - AI-Powered PDF Study Assistant

> Transform your PDF documents into interactive study materials with AI-powered tools!

[![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![Next.js](https://img.shields.io/badge/Next.js-16.0-000000?style=for-the-badge&logo=next.js&logoColor=white)](https://nextjs.org/)
[![Groq](https://img.shields.io/badge/Groq-AI-FF6B35?style=for-the-badge)](https://groq.com/)
[![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [API Documentation](#-api-documentation)
- [Project Structure](#-project-structure)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌟 Overview

**SubRevision** is an intelligent study companion that leverages AI to help students learn more effectively. Upload any PDF document and instantly generate:

- ❓ **Q&A System** - Ask questions and get context-aware answers
- 🔍 **Smart Search** - Find relevant content quickly
- 📝 **Auto Summaries** - Get comprehensive document summaries
- 🎯 **Interactive Quizzes** - Test your knowledge with auto-generated questions
- 🃏 **3D Flashcards** - Flip-to-learn with beautiful card animations
- 🧠 **Mind Maps** - Visualize concepts hierarchically
- 📅 **Study Plans** - Get personalized day-by-day study schedules

---

## ✨ Features

### 🎯 Core Features

| Feature | Description | Status |
|---------|-------------|--------|
| **PDF Upload** | Process and store PDF documents up to 50MB | ✅ Active |
| **AI Q&A** | Ask questions about your document content | ✅ Active |
| **Semantic Search** | Find relevant sections with vector search | ✅ Active |
| **Auto Summary** | Generate concise summaries of entire documents | ✅ Active |
| **Quiz Generation** | Create multiple-choice questions with answers | ✅ Active |
| **Flashcards** | Generate interactive flip cards for memorization | ✅ Active |
| **Mind Mapping** | Build hierarchical concept maps | ✅ Active |
| **Study Plans** | Get structured multi-day learning schedules | ✅ Active |

### 🎨 UI Features

- 🎮 **Pixel Art Theme** - Retro-inspired, midnight study aesthetic
- 🌙 **Dark Mode** - Easy on the eyes for late-night studying
- 📱 **Responsive Design** - Works on desktop, tablet, and mobile
- ⚡ **Real-time Loading States** - Visual feedback for all operations
- 🎭 **Interactive Components** - Click-to-reveal answers, flip cards
- 🎨 **Color-coded Content** - Different colors for different content types

---

## 🛠 Tech Stack

### Backend
- **FastAPI** - High-performance Python web framework
- **Groq API** - Ultra-fast AI inference with Llama 3.3 70B
- **PyPDF2** - PDF text extraction
- **Python 3.12** - Modern Python runtime
- **Uvicorn** - ASGI server for production

### Frontend
- **Next.js 16** - React framework with App Router
- **React 19** - Latest React with concurrent features
- **TypeScript 5** - Type-safe JavaScript
- **Tailwind CSS 4** - Utility-first CSS framework
- **Turbopack** - Next-gen bundler (dev mode)

### AI & ML
- **Groq Cloud** - Free AI API with 30 req/min, 14,400 req/day
- **Llama 3.3 70B Versatile** - State-of-the-art LLM
- **JSON Vector Storage** - Lightweight document storage

---

## 📋 Prerequisites

Before you begin, ensure you have:

- **Python 3.12+** ([Download](https://www.python.org/downloads/))
- **Node.js 20+** & **npm** ([Download](https://nodejs.org/))
- **Git** ([Download](https://git-scm.com/))
- **Groq API Key** (Free at [console.groq.com](https://console.groq.com/))

---

## 🚀 Installation

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/muskiteer/SubRevision.git
cd SubRevision
```

### 2️⃣ Backend Setup

```bash
# Navigate to backend directory
cd backend

# Create virtual environment
python3 -m venv .venv

# Activate virtual environment
# On Linux/Mac:
source .venv/bin/activate
# On Windows:
# .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 3️⃣ Frontend Setup

```bash
# Navigate to frontend directory (from project root)
cd frontend

# Install dependencies
npm install
```

---

## ⚙️ Configuration

### Backend Configuration

Create a `.env` file in the `backend/` directory:

```bash
cd backend
touch .env
```

Add your Groq API key:

```env
GROQ_API_KEY=your_groq_api_key_here
```

**Get Your Free Groq API Key:**
1. Visit [console.groq.com](https://console.groq.com/)
2. Sign up/Login
3. Navigate to API Keys
4. Create new key
5. Copy and paste into `.env`

### Frontend Configuration

The frontend is pre-configured to connect to `http://localhost:8000` (backend).

If you need to change the API URL, edit `frontend/app/page.tsx`:

```typescript
const API_BASE = 'http://localhost:8000'; // Change if needed
```

---

## 🎮 Usage

### Starting the Application

#### Option 1: Run Both Servers Separately

**Terminal 1 - Backend:**
```bash
cd backend
source .venv/bin/activate  # Activate virtual environment
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
```

#### Option 2: Background Mode

```bash
# Start backend in background
cd backend && source .venv/bin/activate && uvicorn main:app --reload &

# Start frontend in background
cd frontend && npm run dev &
```

### Accessing the Application

- **Frontend:** http://localhost:3000
- **Backend API:** http://localhost:8000
- **API Docs:** http://localhost:8000/docs (Swagger UI)
- **Alternative API Docs:** http://localhost:8000/redoc (ReDoc)

---

## 📚 API Documentation

### Endpoints

#### 📄 PDF Management

```http
POST /pdf/upload
Content-Type: multipart/form-data
```
Upload a PDF file for processing.

**Request:**
- `file`: PDF file (max 50MB)

**Response:**
```json
{
  "status": "success",
  "message": "PDF processed successfully",
  "filename": "document.pdf",
  "text_length": 5420,
  "num_chunks": 12,
  "embeddings_stored": 12
}
```

---

#### ❓ Query Operations

```http
POST /query/ask
Content-Type: application/json
```
Ask questions about the uploaded document.

**Request:**
```json
{
  "query": "What is the main topic of this document?"
}
```

**Response:**
```json
{
  "status": "success",
  "query": "What is the main topic...",
  "answer": "The main topic is...",
  "context_used": 3
}
```

---

```http
POST /query/search
Content-Type: application/json
```
Search for relevant sections in the document.

**Request:**
```json
{
  "query": "machine learning algorithms"
}
```

**Response:**
```json
{
  "status": "success",
  "query": "machine learning algorithms",
  "results_count": 5,
  "results": [
    {
      "chunk_id": 3,
      "text": "Machine learning algorithms...",
      "relevance": "high"
    }
  ]
}
```

---

#### 🎯 Generation Operations

```http
POST /generate/summary
```
Generate a comprehensive summary.

**Response:**
```json
{
  "status": "success",
  "summary": "**Main Topic:** ...\n**Key Points:**\n- Point 1\n...",
  "text_length_analyzed": 4000
}
```

---

```http
POST /generate/quiz
Content-Type: application/json
```
Generate interactive quiz questions.

**Request:**
```json
{
  "num_questions": 5,
  "difficulty": "medium"
}
```

**Response:**
```json
{
  "status": "success",
  "quiz": {
    "questions": [
      {
        "question": "What is...?",
        "options": ["A", "B", "C", "D"],
        "answer": "A",
        "explanation": "Because..."
      }
    ]
  }
}
```

---

```http
POST /generate/flashcards
Content-Type: application/json
```
Generate flashcards for memorization.

**Request:**
```json
{
  "num_cards": 10
}
```

**Response:**
```json
{
  "status": "success",
  "flashcards": {
    "flashcards": [
      {
        "front": "What is X?",
        "back": "X is..."
      }
    ]
  }
}
```

---

```http
POST /generate/mindmap
```
Generate a hierarchical mind map.

**Response:**
```json
{
  "status": "success",
  "mindmap": {
    "title": "Main Topic",
    "children": [
      {
        "title": "Subtopic 1",
        "description": "Details...",
        "children": [...]
      }
    ]
  }
}
```

---

```http
POST /generate/studyplan
Content-Type: application/json
```
Generate a structured study plan.

**Request:**
```json
{
  "duration_days": 7
}
```

**Response:**
```json
{
  "status": "success",
  "study_plan": {
    "days": [
      {
        "day": 1,
        "title": "Introduction",
        "topics": ["Topic 1", "Topic 2"],
        "tasks": ["Read chapter 1", "Practice exercises"],
        "duration": "2 hours"
      }
    ]
  }
}
```

---

## 📁 Project Structure

```
SubRevision/
├── backend/                    # Python FastAPI backend
│   ├── db/                     # Database layer
│   │   ├── db.py              # Vector storage implementation
│   │   └── __init__.py
│   ├── handlers/              # Business logic
│   │   ├── handler.py         # API request handlers
│   │   └── __init__.py
│   ├── routes/                # API routes
│   │   ├── routes.py          # Endpoint definitions
│   │   └── __init__.py
│   ├── utils/                 # Utility functions
│   │   ├── pdf_processor.py  # PDF extraction logic
│   │   └── __init__.py
│   ├── main.py                # FastAPI application entry
│   ├── requirements.txt       # Python dependencies
│   ├── .env                   # Environment variables (create this)
│   └── GROQ_SETUP.md         # Groq API setup guide
│
├── frontend/                  # Next.js frontend
│   ├── app/                   # Next.js App Router
│   │   ├── layout.tsx        # Root layout
│   │   ├── page.tsx          # Main page component
│   │   └── globals.css       # Global styles (pixel theme)
│   ├── public/               # Static assets
│   ├── package.json          # Node dependencies
│   ├── tsconfig.json         # TypeScript config
│   ├── next.config.ts        # Next.js config
│   ├── tailwind.config.ts    # Tailwind config
│   └── postcss.config.mjs    # PostCSS config
│
└── README.md                  # This file
```

---

## 🎨 UI Components

### Tab Navigation
8 tabs for different features:
- 📄 Upload PDF
- ❓ Ask Query
- 🔍 Search
- 📝 Summary
- 🎯 Quiz
- 🃏 Flashcards
- 🧠 Mind Map
- 📅 Study Plan

### Interactive Elements

**Quiz Questions:**
- Click "Show Answer" to reveal
- Color-coded: Question (cyan) → Answer (green)
- Smooth fade-in animations

**Flashcards:**
- 3D flip animation on click
- Front: Cyan border (question)
- Back: Green border (answer)
- Responsive grid layout

**Mind Map:**
- Hierarchical tree structure
- Color-coded by depth level
- Expandable/collapsible nodes

**Study Plan:**
- Day-by-day cards
- Topics with cyan bullets
- Tasks with yellow checkboxes
- Duration indicators

---

## 🔧 Development

### Running Tests

```bash
# Backend tests (if available)
cd backend
pytest

# Frontend tests (if available)
cd frontend
npm test
```

### Building for Production

**Backend:**
```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --host 0.0.0.0 --port 8000
```

**Frontend:**
```bash
cd frontend
npm run build
npm start
```

### Docker Deployment (Optional)

Create `Dockerfile` in backend:
```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

Create `Dockerfile` in frontend:
```dockerfile
FROM node:20-alpine
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
RUN npm run build
CMD ["npm", "start"]
```

---

## 🐛 Troubleshooting

### Common Issues

**1. "No PDF uploaded yet" error**
- Make sure to upload a PDF before using other features
- Check if upload was successful (status message)

**2. Backend connection refused**
- Verify backend is running on port 8000
- Check CORS settings in `backend/main.py`
- Ensure firewall allows port 8000

**3. Groq API errors**
- Verify API key in `.env` file
- Check API quota (30 req/min, 14,400 req/day)
- Ensure no extra spaces in API key

**4. Frontend not connecting to backend**
- Check `API_BASE` URL in `frontend/app/page.tsx`
- Verify backend is accessible at that URL
- Check browser console for CORS errors

**5. PDF upload fails**
- Ensure file is under 50MB
- Check file is valid PDF format
- Verify backend has write permissions

---

## 📊 Performance

### Groq API Limits
- **Rate Limit:** 30 requests/minute
- **Daily Limit:** 14,400 requests/day
- **Model:** llama-3.3-70b-versatile
- **Speed:** ~1000 tokens/second
- **Cost:** FREE ✨

### Backend Performance
- Handles PDFs up to 50MB
- Chunks text into 500-char segments
- Stores vectors in JSON (lightweight)
- CORS enabled for localhost:3000

### Frontend Performance
- Next.js 16 with Turbopack (dev)
- React 19 concurrent rendering
- Client-side state management
- No external API calls except backend

---

## 🤝 Contributing

We welcome contributions! Here's how:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add AmazingFeature'`)
4. **Push** to branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Development Guidelines
- Follow PEP 8 for Python code
- Use ESLint/Prettier for TypeScript
- Add comments for complex logic
- Update README for new features
- Test before submitting PR

---


## 🌟 Acknowledgments

- **Groq** for providing free, ultra-fast AI inference
- **Meta** for the Llama 3.3 model
- **FastAPI** for the excellent Python framework
- **Vercel** for Next.js and amazing developer experience
- **Tailwind CSS** for the utility-first CSS framework

---

## 📞 Support

- **Issues:** [GitHub Issues](https://github.com/muskiteer/SubRevision/issues)
- **Discussions:** [GitHub Discussions](https://github.com/muskiteer/SubRevision/discussions)
- **Email:** support@subrevision.dev (if available)

---

## 🗺️ Roadmap

### Coming Soon
- [ ] Multiple PDF support
- [ ] Export quiz to PDF
- [ ] Voice Q&A
- [ ] Collaborative study rooms
- [ ] Mobile app (React Native)
- [ ] Chrome extension
- [ ] Integration with learning platforms

### Future Ideas
- [ ] Video lecture summarization
- [ ] Spaced repetition system
- [ ] Progress tracking & analytics
- [ ] Social features (share cards/quizzes)
- [ ] Multi-language support
- [ ] OCR for scanned PDFs

---

<div align="center">

### Made with 💜 for Students

**Star ⭐ this repo if you find it helpful!**


</div>
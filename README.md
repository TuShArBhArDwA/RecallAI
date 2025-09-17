# RecallAI

<img width="1918" height="1027" alt="image" src="https://github.com/user-attachments/assets/78571971-774f-4d7d-9f04-0e555672d5c5" />


A scalable conversational AI platform built with FastAPI and LangGraph, designed for multi-tenant deployments, advanced memory handling, and real-time voice chat via LiveKit.

---

## 📑 Table of Contents
- [Overview](#overview)
- [Core Highlights](#core-highlights)
- [Backend Architecture](#backend-architecture)
- [Usage Guide](#usage-guide)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [Contributing](#contributing)
- [Contact](#contact)
- [License](#license)

---


## Overview

RecallAI combines modern backend architecture with advanced orchestration and memory features to deliver an intelligent chatbot system. It supports both text and voice interactions, enabling enterprises and developers to build AI assistants that remember past conversations, coordinate across multiple agents, and scale securely for multi-tenant environments.

---

## Core Highlights

### Authentication & Multi-Tenancy
- OAuth2 authentication with JWT tokens
- User registration and tenant isolation for secure data handling
- Role-based permissions for fine-grained access control

### Multi-Agent Orchestration (LangGraph)
- Supervisor agent for workflow coordination
- Research agent for knowledge retrieval
- Scraper agent for summarizing web content
- Handles multi-step workflows with persistent context

### Vector Search with Qdrant
- Tenant-specific vector storage for embeddings
- Semantic search across conversation history
- Metadata and payload filtering for efficient lookups

### Persistent Memory (Mem0)
- Cross-session and cross-chat memory
- Selective long-term storage of key facts
- Context-aware retrieval of relevant memory

### MCP Tool Integration
- Firecrawl for structured web scraping and summarization
- Tavily for semantic, real-time web search

### Voice Mode (LiveKit)
- Voice conversations powered by WebRTC
- Deepgram STT and Cartesia TTS for natural speech
- Voice activity detection for smooth interaction
- Multilingual support

### Observability with LangSmith
- Execution tracing and debugging
- Token usage and latency monitoring
- Feedback collection and experiment tracking

### Web UI
- React frontend with Material UI
- Responsive design with chat bubbles and avatars
- Markdown rendering for rich responses
- Switch between text and voice modes seamlessly

---

## Backend Architecture

- FastAPI backend with async APIs
- SQLAlchemy + SQLite/Postgres for persistence
- Qdrant for vector storage
- Pydantic models for validation
- JWT/OAuth2 for authentication
- React frontend with real-time chat

---
## Usage Guide

### Getting Started

1. **Sign Up**  
   - Visit `/register` to create your account  
   - Provide a username, password, and tenant_id  
   - Each tenant_id ensures that your data remains isolated and private  

2. **Log In**  
   - Log in from the main page using your credentials  
   - A JWT token is generated and stored securely for your API requests  

---

### Chat Interface

1. **Start a New Conversation**  
   - Use the "+" button in the sidebar to create a conversation  
   - Assign a meaningful title for quick reference later  
   - Conversations are saved under your tenant_id  

2. **Chatting with the Assistant**  
   - Enter a message in the text box and press Enter or click Send  
   - Responses stream back in real-time, token by token  
   - Messages include user/assistant avatars for clarity  
   - Markdown is supported for formatting responses  

3. **Manage Conversations**  
   - Access older chats directly from the sidebar  
   - Search through past sessions easily  

---

### Voice Assistant

1. **Enable Voice Mode**  
   - Click the microphone button in the chat window  
   - Allow microphone access when prompted  
   - Wait for the "Ready" indicator before speaking  

2. **Voice Conversations**  
   - Speak naturally when the "Listening..." message appears  
   - The assistant transcribes and replies with speech  
   - Both your speech and the AI’s response appear on screen  

3. **Extra Voice Features**  
   - Automatic detection when you stop speaking  
   - Noise filtering with voice activity detection (VAD)  
   - Multilingual conversation support  
   - Adjustable settings for voice quality  

4. **Close Voice Session**  
   - Click the disconnect button to end the session  
   - All history remains saved with your account  

---

### External Tools

The assistant can extend its capabilities through integrated tools:

- **Web Search** – Retrieve fresh, up-to-date information  
- **Web Scraping** – Summarize or extract details from specific pages  

---

## Installation

### Requirements

Before you begin, ensure you have the following installed:

- Python 3.13 or higher
- Node.js 16+ and npm 8+
- Qdrant (local install or via Docker)


### Backend Setup

1. Clone the repository

```bash
git clone https://github.com/TuShArBhArDwA/RecallAI
cd RecallAI
```

2. Set Up a Virtual Environment

```bash
python -m venv venv
# Activate
source venv/bin/activate       # macOS/Linux
venv\Scripts\activate          # Windows
```

3. Install Dependencies

```bash
pip install -r requirements.txt
```

4. Configure Environment Variables

Create a `.env` file in the project root with the following values:

```env
# FastAPI
SECRET_KEY=your_secret_key
ACCESS_TOKEN_EXPIRE_MINUTES=30

# Database
SQLALCHEMY_DATABASE_URI=sqlite:///./app.db

# OpenAI
OPENAI_API_KEY=your_openai_api_key

# Qdrant
QDRANT_HOST=localhost
QDRANT_PORT=6333

# LiveKit
LIVEKIT_URL=your_livekit_url
LIVEKIT_API_KEY=your_livekit_api_key
LIVEKIT_API_SECRET=your_livekit_api_secret

# LangSmith (optional)
LANGCHAIN_TRACING_V2=true
LANGSMITH_API_KEY=your_langsmith_api_key
LANGSMITH_PROJECT=your_project_name
```

### Frontend Setup

1. Move to the frontend folder

```bash
cd frontend
```

2. Install Packages

```bash
npm install
```

---

## Running the Application

### Backend

1. Start the MCP Tool Servers (each in a new terminal)

```bash
# Search service
python -m app.mcp_server.search_server

# Web scraping service
python -m app.mcp_server.web_scrapping_server
```

2. Start FastAPI

```bash
python app.py
```

3. Start the LiveKit voice assistant

```bash
python app/agent/livekit_agent.py dev
```

### Frontend

```bash
cd frontend
npm start
```

### Access

- Frontend interface: http://localhost:3000


---

## Contributing
Feel free to fork this repository and submit pull requests if you have suggestions or improvements.  
- For bug reports or feature requests, please [open an issue](../../issues).  
- All contributions (bug fixes, new features, docs improvements) are welcome!  

---

## Contact
- **Meet T-Bot** - [Discover My Work](https://t-bot-blush.vercel.app/)
- **Tushar Bhardwaj** - [Portfolio](https://tushar-bhardwaj.vercel.app/)
- **Connect 1:1** - [Topmate](https://topmate.io/tusharbhardwaj)
- **GitHub:** [TuShArBhArDwA](https://github.com/TuShArBhArDwA)
- **LinkedIn:** [Tushar Bhardwaj](https://www.linkedin.com/in/bhardwajtushar2004/)
- **Email:** [tusharbhardwaj2617@example.com](mailto:tusharbhardwaj2617@example.com)

---

## License
This project is licensed under the **MIT License**.  
See the [LICENSE](./LICENSE) file for details.  


If you don't have an account, register first and then log in to access the chat interface.


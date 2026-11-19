# Law Simplified — Multi-Agent Legal AI Platform

An AI-powered legal assistance platform combining **multi-agent orchestration, Retrieval-Augmented Generation (RAG), semantic search, vector embeddings and legal knowledge graph visualization** to support document-grounded legal research across multiple domains.

[![Node.js](https://img.shields.io/badge/Node.js-Backend-green)](https://nodejs.org/)
[![React](https://img.shields.io/badge/React-Frontend-blue)](https://react.dev/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Database-green)](https://www.mongodb.com/)
[![Pinecone](https://img.shields.io/badge/Pinecone-Vector%20Database-purple)](https://www.pinecone.io/)
[![LangChain](https://img.shields.io/badge/LangChain-LLM%20Framework-blue)](https://www.langchain.com/)

---

## Overview

Law Simplified is a full-stack AI legal assistance platform designed to make legal document analysis and research more accessible and organized.

The platform combines specialized AI agents with document retrieval to process legal queries and analyze client submissions across four domains:

- Civil Law
- Criminal Law
- Corporate Law
- Tax Law

Rather than relying on a single general-purpose LLM response, the application uses an orchestrator to coordinate domain-specific agents, retrieve relevant legal document context and generate structured analysis.

The platform supports two primary workflows:

**General Mode**
- Ask legal questions in natural language.
- Retrieve relevant context from indexed legal PDFs.
- Generate context-aware responses.
- Access English, Hindi and Marathi interfaces and responses.
- Use voice input and audio responses.

**Lawyer Mode**
- Submit detailed client case descriptions.
- Run parallel analysis through specialized legal-domain agents.
- Compare findings across legal domains.
- Generate structured conflict reports.
- Explore relationships through an interactive legal knowledge graph.
- Manage client interactions and case sessions.

## Key Features

### 1. Multi-Agent Orchestration

An agent orchestration layer coordinates specialized legal agents:

- Civil Agent
- Criminal Agent
- Corporate Agent
- Tax Agent
- Comparison Agent
- Report Agent

In Lawyer Mode, the four domain agents analyze the submitted case in parallel. Their findings are processed through comparison and report-generation stages.

### 2. Retrieval-Augmented Generation (RAG)

Implemented a document-based retrieval pipeline:

1. Upload legal PDF documents.
2. Extract document text.
3. Apply OCR fallback for scanned or unreadable PDFs.
4. Split extracted content into overlapping text chunks.
5. Generate vector embeddings.
6. Store vectors and document metadata in Pinecone.
7. Rewrite user queries for contextual retrieval.
8. Retrieve relevant document passages.
9. Generate responses using retrieved context.

The retrieval pipeline uses Pinecone vector search and LLM integrations through Groq and Google Gemini.

### 3. Legal Knowledge Graph

The platform includes a legal graph data model and interactive graph visualization.

It supports:
- Session and message relationships.
- Legal section and citation relationships.
- Connections between related legal provisions.
- Interactive exploration of graph nodes.
- Contextual follow-up questions about selected nodes.

The graph functionality complements the document-retrieval workflow by making relationships and analysis results easier to explore.

### 4. LLM Integration

Integrates multiple LLM services for different application workflows:

- Groq for language-model inference.
- Google Gemini for model fallback and multimodal processing.
- Prompt-based domain-specific agent behavior.
- Contextual query rewriting.
- Structured JSON response parsing.
- Response translation and generation.

### 5. Multilingual and Voice Processing

Supports:
- English
- Hindi
- Marathi

Additional capabilities:
- Language translation.
- Speech-to-text transcription.
- Text-to-speech generation.
- Voice-based legal query interaction.

### 6. Document and Client Management

- JWT-based authentication.
- Role-based access for users, lawyers and administrators.
- MongoDB-backed user and conversation management.
- PDF document upload and management.
- Cloudinary document storage.
- Client and case session organization.
- PDF and Excel report exports.

---

## System Architecture

```text
                  REACT + VITE FRONTEND
                           |
                    REST API Requests
                           |
                 NODE.JS + EXPRESS BACKEND
                           |
                  AGENT ORCHESTRATOR
                           |
             +-------------+-------------+
             |             |             |
         CIVIL AGENT  CRIMINAL AGENT  CORPORATE AGENT
             |             |             |
             +-------------+-------------+
                           |
                       TAX AGENT
                           |
                    RETRIEVAL AGENT
                           |
                  PINECONE VECTOR SEARCH
                           |
                  RETRIEVED LEGAL CONTEXT
                           |
                   GENERAL / DOMAIN AGENTS
                           |
                   COMPARISON AGENT
                           |
                     REPORT AGENT
                           |
                  STRUCTURED AI RESPONSE
                           |
             +-------------+-------------+
             |             |             |
         MONGODB       LEGAL GRAPH     FRONTEND
                         |
                  GRAPH VISUALIZATION
```

### Document Ingestion Workflow

```text
Legal PDF Upload
       |
       v
Cloudinary Storage
       |
       v
PDF Text Extraction
       |
       v
OCR Fallback (Gemini Vision)
       |
       v
Recursive Text Chunking
       |
       v
Embedding Generation
       |
       v
Pinecone Vector Index
       |
       v
Semantic Retrieval
       |
       v
LLM Response Generation
```

---

## Technology Stack

| Layer | Technologies |
|---|---|
| Frontend | React, Vite, JavaScript |
| Styling | Tailwind CSS |
| Backend | Node.js, Express.js |
| Database | MongoDB, Mongoose |
| LLM Integration | Groq, Google Gemini |
| AI Orchestration | LangChain, Custom Agent Orchestrator |
| Vector Database | Pinecone |
| Retrieval | Embeddings, Semantic Search, RAG |
| Document Processing | LangChain PDFLoader, Gemini Vision OCR |
| Speech Processing | Gemini Speech-to-Text and Text-to-Speech |
| Authentication | JWT, bcryptjs |
| Cloud Storage | Cloudinary |
| Graph Visualization | Three.js, react-force-graph-3d |
| Report Generation | PDFKit, ExcelJS |

---

## Project Structure

```text
law-simplified-ai/
|
|-- backend/
|   |-- config/
|   |-- controllers/
|   |-- middleware/
|   |-- models/
|   |-- routes/
|   |-- services/
|   |   |-- agentOrchestrator.js
|   |   |-- agentPrompts.js
|   |   |-- ragService.js
|   |   |-- retrievalAgent.js
|   |   |-- civilAgent.js
|   |   |-- criminalAgent.js
|   |   |-- corporateAgent.js
|   |   |-- taxAgent.js
|   |   |-- comparisonAgent.js
|   |   |-- reportAgent.js
|   |   |-- translationService.js
|   |   |-- speechService.js
|   |   |-- storageService.js
|   |-- scripts/
|   |-- app.js
|   |-- package.json
|   |-- .env.example
|
|-- frontend/
|   |-- public/
|   |-- src/
|   |   |-- components/
|   |   |-- context/
|   |   |-- hooks/
|   |   |-- lib/
|   |   |-- pages/
|   |   |-- App.jsx
|   |   |-- main.jsx
|   |-- package.json
|   |-- vite.config.js
|
|-- .gitignore
|-- README.md
```

---

## Getting Started

### Prerequisites

- Node.js 18+
- npm
- MongoDB database
- Pinecone account and API key
- Groq API key
- Google Gemini API key
- Cloudinary account

### 1. Clone the repository

```bash
git clone https://github.com/pranavingle/law-simplified-ai.git

cd law-simplified-ai
```

### 2. Configure the backend

```bash
cd backend

npm install --legacy-peer-deps
```

Create a `.env` file using `.env.example`.

Configure the required environment variables:

```env
PORT=5001

MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret

PINECONE_API_KEY=your_pinecone_api_key
PINECONE_INDEX_NAME=your_pinecone_index

GEMINI_API_KEY=your_gemini_api_key
GROQ_API_KEY=your_groq_api_key

CLOUDINARY_CLOUD_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
```

Start the backend:

```bash
npm run dev
```

Backend default development URL:

```text
http://localhost:5001
```

### 3. Configure the frontend

Open a separate terminal:

```bash
cd frontend

npm install --legacy-peer-deps
```

Start the frontend:

```bash
npm run dev
```

Frontend URL:

```text
http://localhost:3000
```

The frontend API client and Vite development proxy are configured for the backend on port 5001. Keep the backend port and frontend API configuration consistent.

---

## Core API Routes

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/auth/register` | User registration |
| POST | `/api/auth/login` | User login |
| GET | `/api/auth/me` | Current user |
| POST | `/api/query` | Submit legal query |
| GET | `/api/query/history` | Retrieve chat history |
| GET | `/api/query/export` | Export analysis report |
| POST | `/api/admin/upload` | Upload legal PDF |
| POST | `/api/admin/process` | Process and index document |
| GET | `/api/graph/session/:sessionId` | Retrieve session graph |
| GET | `/api/graph/project` | Retrieve project graph |
| POST | `/api/speech/transcribe` | Speech transcription |
| POST | `/api/speech/synthesize` | Text-to-speech |

See [`backend/API_DOCS.md`](backend/API_DOCS.md) for detailed request formats, authentication requirements and response examples.

---

## My Contributions

My contributions to the project covered architecture, implementation and integration across major application modules:

- Designed and integrated the multi-agent orchestration workflow and specialized legal-domain agents.
- Implemented the RAG document-processing pipeline, embedding generation and Pinecone vector integration.
- Integrated Groq and Gemini models, prompt engineering, contextual query rewriting and structured response parsing.
- Developed legal knowledge graph models, graph APIs and visualization integration.
- Implemented multilingual translation, document OCR fallback and speech-processing workflows.
- Developed backend APIs, authentication, MongoDB persistence and frontend application workflows.
- Contributed to end-to-end architecture, module integration and application validation.

This was a collaborative project; the above describes my areas of contribution.

---

## Security and Limitations

- Never commit API keys, database credentials, JWT secrets or private configuration files.
- Keep user documents and uploaded legal records private.
- Authentication and authorization should be configured before exposing the application publicly.
- AI-generated legal information can be incomplete or incorrect and must be independently verified.
- The platform is intended for legal research assistance and educational use, not as a substitute for advice from a qualified legal professional.
- Retrieval quality depends on the quality, completeness and currency of indexed legal documents.

## Current Development Status

This repository represents a working project implementation with core AI, retrieval, backend and frontend modules.

Further engineering improvements include expanded automated test coverage, reproducible containerized deployment, systematic RAG evaluation and stronger production monitoring.

## License

No open-source license is currently granted. Contact the project contributors before reusing or redistributing this code.

---

**Built with a focus on multi-agent AI, document intelligence and practical full-stack engineering.**

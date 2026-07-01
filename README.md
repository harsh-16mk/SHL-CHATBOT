# SHL Assessment Recommender API

A conversational AI-powered assessment recommendation system developed for the **SHL GenAI Internship Assignment**.

The application uses **Google Gemini 2.0 Flash** together with **Retrieval-Augmented Generation (RAG)** using **Sentence Transformers** and **FAISS** to recommend relevant SHL assessments based on user requirements.

---

# Features

- Conversational AI assessment recommender
- Asks clarifying questions when user input is incomplete
- Semantic search using FAISS and Sentence Transformers
- Grounded recommendations using SHL assessment catalog
- Assessment comparison based on catalog evidence
- Stateless conversation API
- FastAPI backend
- Interactive Swagger API documentation
- Railway deployment

---

# Tech Stack

- Python
- FastAPI
- Google Gemini 2.0 Flash
- Sentence Transformers (all-MiniLM-L6-v2)
- FAISS
- Pydantic
- Uvicorn

---

# Project Structure

```text
.
|-- main.py
|-- retriever.py
|-- catalog.json
|-- evaluate_traces.py
|-- requirements.txt
|-- README.md
`-- GenAI_SampleConversations_Traces/
```

---

# Local Setup

## Install dependencies

```bash
pip install -r requirements.txt
```

## Configure Environment Variables

Create a `.env` file in the project root:

```env
GEMINI_API_KEY=YOUR_GEMINI_API_KEY
```

## Run the application

```bash
uvicorn main:app --reload
```

The API will be available at:

```text
http://127.0.0.1:8000
```

Swagger documentation:

```text
http://127.0.0.1:8000/docs
```

---

# Live Deployment

**Base URL**

```text
https://shl-chatbot-production-0a32.up.railway.app
```

**Swagger Documentation**

```text
https://shl-chatbot-production-0a32.up.railway.app/docs
```

**Health Endpoint**

```text
GET https://shl-chatbot-production-0a32.up.railway.app/health
```

---

# API Endpoints

## Health Check

```text
GET /health
```

Response

```json
{
  "status": "ok"
}
```

---

## Chat

```text
POST /chat
```

Example Request

```json
{
  "messages": [
    {
      "role": "user",
      "content": "Recommend an assessment for a Java Developer with 3 years of experience."
    }
  ]
}
```

---

# Retrieval Pipeline

1. User submits a query.
2. The query is converted into embeddings using Sentence Transformers.
3. FAISS retrieves the most relevant SHL assessments.
4. Retrieved assessments are supplied as context to Gemini.
5. Gemini generates grounded recommendations.
6. The API returns the final response.

---

# Evaluation

The system was evaluated using:

- `evaluate_traces.py`
- Sample conversation traces
- Retrieval quality
- Recommendation relevance
- Groundedness against the SHL catalog
- Overall response accuracy

---

# LLM Used

**Google Gemini 2.0 Flash**

---

# Deployment

Hosted on **Railway**

API Documentation:

https://shl-chatbot-production-0a32.up.railway.app/docs

Health Endpoint:

https://shl-chatbot-production-0a32.up.railway.app/health

---

# Author

**Harsh**

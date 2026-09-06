# VikriMitra — E-Commerce Sales Analytics Chatbot

VikriMitra is an AI-powered e-commerce sales analytics chatbot that converts plain-English business questions into database-backed analytics, charts, and concise insights.

## Features

- Natural-language sales analytics queries
- Groq-powered LLM agent with native tool calling
- Rule-based fallback mode
- MCP-based analytics tool layer
- PostgreSQL database with the complete Olist Brazilian E-Commerce dataset
- Revenue, orders, products, sellers, reviews, payments, and delivery analytics
- Automatic chart selection
- Scatter plots for relationship analysis
- Persistent dashboard with pinned charts
- Dashboard refresh against current database data
- Structured JSON error handling
- Docker Compose deployment

## Architecture

```text
React + Vite Frontend
        |
        v
FastAPI API
        |
        v
AI Agent (Groq / Fallback)
        |
        v
MCP Analytics Server
        |
        v
PostgreSQL
        ^
        |
   Olist CSV Dataset

## Technology Stack

- Python 3.11
- FastAPI
- SQLAlchemy
- PostgreSQL 16
- MCP Python SDK
- Groq API
- React
- Vite
- Chart.js
- Docker / Docker Compose

## MCP Analytics Tools

The MCP server exposes the following analytics tools:

1. Order trends
2. Product/category performance
3. Seller performance
4. Customer review analysis
5. Payment breakdown
6. Delivery performance

All MCP tools return structured JSON responses, including structured errors instead of propagating exceptions.

## Agent Modes

The application supports two agent modes through `AGENT_MODE`:

- `llm` — Groq-powered native tool calling
- `fallback` — deterministic rule-based query handling

Example:

```env
AGENT_MODE=llm
GROQ_MODEL=openai/gpt-oss-20b
LLM_TIMEOUT_SECONDS=15
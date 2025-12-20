# StockVibe

StockVibe is a lightweight stock analytics dashboard that combines real-time price data, historical charts, and simple sentiment analysis of news headlines to help you explore market sentiment and price trends quickly.

This repository contains a small Python backend (API + optional WebSocket) and a minimal frontend (static HTML/JS) that demonstrates how to fetch and visualize stock data and sentiment.

## Quick overview

- Backend: `backend/main.py` (Python + FastAPI)
- Frontend: `frontend/index.html` (vanilla HTML/CSS/JS)
- Purpose: demo/POC for stock price visualization + news sentiment

## Features

- Search for stock symbols and fetch recent price data
- Historical price chart with simple indicators (e.g., moving average)
- News headline sentiment aggregation (uses NewsAPI or similar)
- Minimal responsive dashboard that can be served statically

## Prerequisites

- macOS (or Linux/Windows) with Python 3.8+ installed. The project was developed targeting Python 3.11 but will likely work on 3.8+.
- A News API key (optional, for news-based sentiment). You can get one at https://newsapi.org/.

## Quick start (development)

Open a terminal (zsh). The following commands assume you are in the project root (`/Users/meena/Documents/GitHub/StockVibe`).

1) Create and activate a virtual environment, then install backend dependencies:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r backend/requirements.txt
```

2) Create a `.env` file (project root) with any required keys. Example:

```env
# .env
NEWSAPI_KEY=your_newsapi_key_here
# Optional: other API keys (FINNHUB_API_KEY, etc.) if the backend uses them
```

3) Start the backend API (FastAPI / Uvicorn):

```bash
cd backend
uvicorn main:app --reload --host 127.0.0.1 --port 8000
```

4) Serve the frontend (static) and open it in the browser. You can either open `frontend/index.html` directly or serve it with Python's simple server:

```bash
cd ../frontend
python3 -m http.server 3000
# then open http://localhost:3000 in your browser
```

## API (example)

The backend exposes endpoints to fetch stock data and compute sentiment. The exact endpoints depend on `backend/main.py`. Typical example endpoints you can expect:

- GET /health - health check
- GET /api/search?query=XXX - search symbols
- GET /api/price?symbol=XXX&range=7d - historical price data
- GET /api/news?symbol=XXX - recent news and sentiment for a symbol

Tip: After starting the backend, open http://127.0.0.1:8000/docs to see interactive FastAPI docs.

## Environment variables

- `NEWSAPI_KEY` — API key for NewsAPI (optional but required for news sentiment)
- Any other keys used by the backend (FINNHUB_API_KEY, etc.) — check `backend/main.py` for exact names

## Development notes

- The backend is implemented in Python. Use the virtual environment for any development or dependency changes.
- If you add Python packages, update `backend/requirements.txt` with pinned versions.
- The frontend is intentionally minimal. If you add a build step (Webpack/Vite/etc.), include instructions and a `package.json`.

## Troubleshooting

- If dependencies fail to install, ensure your pip, setuptools, and wheel are up to date:

```bash
python -m pip install --upgrade pip setuptools wheel
```

- If the backend fails to start because a port is in use, change the `--port` value when launching Uvicorn.
- If news endpoints return empty results, verify `NEWSAPI_KEY` is set and valid.

## Next steps / Suggestions

- Add unit tests for backend endpoints and a CI workflow (GitHub Actions) to run them.
- Add an npm-based frontend build if you plan to add React/Vue and modern tooling.
- Add Dockerfiles for reproducible local/dev environments.

## Contact

If you want help extending this project or adding features, open an issue or reach out in the repo's discussions.

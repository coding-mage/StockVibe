
# StockDashboard

A simple analytics dashboard for real-time stock tracking and sentiment analysis.

## Features

- **Stock Search & Curated List:**
  - Search for stocks by symbol or company name.
  - Access a curated list of popular stocks.

- **Real-Time Price Analytics:**
  - Live price updates via WebSocket.
  - Historical price chart with moving averages and volatility.

- **Sentiment Analysis:**
  - News sentiment: Fetches latest news headlines for the selected stock and analyzes their sentiment (summary, most positive/negative headlines).

- **Dashboard UI:**
  - Clean, responsive dashboard built with HTML, CSS, and JavaScript.
  - Interactive charts using Chart.js.

## Tech Used

- **Frontend:**
  - HTML, CSS, JavaScript (vanilla)
  - Chart.js (for analytics visualization)

- **Backend:**
  - Python 3.11+
  - FastAPI (REST API & WebSocket)
  - yfinance (stock data)
  - TextBlob (sentiment analysis)
  - NewsAPI (news headlines)
  - httpx, pandas, python-dotenv

## Setup Instructions

1. **Clone the repository and navigate to the project folder.**

2. **Backend Setup:**
   - Create a Python 3.11+ virtual environment:
     ```sh
     python3.11 -m venv .venv
     source .venv/bin/activate
     ```
   - Install dependencies:
     ```sh
     pip install -r backend/requirements.txt
     ```
   - Create a `.env` file in the project root with your API keys:
     ```env
     NEWSAPI_KEY=your_newsapi_key_here
     FINNHUB_API_KEY=your_finnhub_key_here  # (optional, for symbol search)
     ```
   - Start the backend server:
     ```sh
     cd backend
     uvicorn main:app --reload
     ```

3. **Frontend Setup:**
   - Serve the frontend with a simple HTTP server:
     ```sh
     cd frontend
     python3 -m http.server 3000
     ```
   - Open [http://localhost:3000](http://localhost:3000) in your browser.

## Notes
- For Twitter sentiment, no Twitter API key is required (uses snscrape).
- For news sentiment, you need a free NewsAPI key: https://newsapi.org/
- For symbol search, a free Finnhub API key is recommended: https://finnhub.io/

## License
MIT License

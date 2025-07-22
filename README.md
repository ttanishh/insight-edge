# 📈 InsightEdge — Real-Time Financial News Sentiment API

[![Deploy Status](https://img.shields.io/badge/render-live-green)](https://insight-edge-1.onrender.com/)
[![Python](https://img.shields.io/badge/python-3.10+-blue)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-⚡-green)](https://fastapi.tiangolo.com/)

**InsightEdge** is a microservice that scrapes real-time financial headlines from multiple trusted sources and performs sentiment analysis to provide market insights.

---

## 🌐 Live API

👉 [https://insight-edge-1.onrender.com](https://insight-edge-1.onrender.com)

---

## 🚀 Features

- 🔍 Scrapes top financial news from:
  - Yahoo Finance (Static)
  - Google News (Dynamic via JS)
  - Economic Times (Interactive Forms)
  - CNBC (Lazy-loaded)
- 🧠 Performs sentiment analysis using a pre-trained ML model
- 📊 Returns JSON responses with title, source, link, and sentiment
- 🔌 FastAPI-powered backend for scalability

---

## 📂 API Usage

### `GET /`
Health check route  
**Response**:
```json
{"message": "InsightEdge API is running"}
GET /headlines
Fetches top 10 headlines per source with sentiment.
Query Parameters:

limit (optional): Number of headlines per source (default: 10)

Example:

bash
Copy
Edit
GET https://insight-edge-1.onrender.com/headlines?limit=5
Response:

json
Copy
Edit
{
  "Yahoo Finance": [
    {
      "title": "S&P 500 hits record high...",
      "link": "https://finance.yahoo.com/...",
      "sentiment": "Positive"
    },
    ...
  ],
  "Google News": [...],
  ...
}
🛠️ Local Development
1. Clone the repo
bash
Copy
Edit
git clone https://github.com/ttanishh/insight-edge.git
cd insight-edge
2. Create a virtual environment
bash
Copy
Edit
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
3. Install dependencies
bash
Copy
Edit
pip install -r requirements.txt
4. Run the app locally
bash
Copy
Edit
uvicorn app.main:app --reload
Visit: http://127.0.0.1:8000/docs

📖 API Documentation
Automatically generated Swagger Docs:
👉 /docs
👉 /redoc

✅ Testing
Manual Testing
Use tools like:

Postman

cURL

FastAPI Swagger UI (/docs)

Automated Testing (Optional)
To add unit tests:

Create a file like tests/test_api.py

Use pytest and httpx:

bash
Copy
Edit
pip install pytest httpx
pytest
Example:

python
Copy
Edit
from fastapi.testclient import TestClient
from app.main import app

client = TestClient(app)

def test_root():
    response = client.get("/")
    assert response.status_code == 200
    assert response.json() == {"message": "InsightEdge API is running"}
📦 Deployment (Render)
This project is deployed using Render.

You can fork and redeploy using:

Build Command: pip install -r requirements.txt

Start Command: uvicorn app.main:app --host=0.0.0.0 --port=10000

Python Version: 3.10+

🤝 Contributing
Pull requests and issues are welcome. For major changes, please open an issue first to discuss what you would like to change.

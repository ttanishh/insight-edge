# 📈 InsightEdge – Stock Market News Sentiment Analyzer

**InsightEdge** is a powerful microservice that scrapes top financial news sources, analyzes headline sentiment, and delivers actionable insights through a blazing-fast REST API built with FastAPI.

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![FastAPI](https://img.shields.io/badge/FastAPI-💚-success)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

---

## 🚀 Features

- ✅ Scrapes headlines from top financial news portals:
  - Yahoo Finance (static)
  - Google News (dynamic JS-rendered)
  - Economic Times (interactive form)
  - CNBC (delayed/lazy-loaded)
- 🔬 Performs sentiment analysis on headlines using VADER/TextBlob
- ⚡ Exposes an easy-to-use FastAPI backend with full Swagger documentation
- 🌐 Designed as a microservice — perfect for integrations or dashboards

---

## 📦 Project Structure

insight-edge/
├── app/
│ ├── main.py # FastAPI server + endpoints
│ ├── scraper.py # News scraping functions
│ ├── sentiment.py # Sentiment analysis logic
│ └── utils.py # Helper utilities
├── requirements.txt # Python dependencies
├── build.sh # Render deployment script
└── README.md

yaml
Copy
Edit

---

## 🧑‍💻 Local Development

### 1. Clone & Install

```bash
git clone https://github.com/ttanishh/insight-edge.git
cd insight-edge
pip install -r requirements.txt
playwright install
⚠️ playwright install is required to run dynamic scrapers (like Google News & CNBC)

2. Run API Locally
bash
Copy
Edit
uvicorn app.main:app --reload
Visit: http://localhost:8000/docs for Swagger UI.

☁️ Deploy on Render (No Dockerfile)
Go to https://render.com and click New Web Service

Connect your GitHub repo and use these settings:

Setting	Value
Build Command	bash build.sh
Start Command	uvicorn app.main:app --host=0.0.0.0 --port=10000
Python Version	3.10+ (auto-detected or set via runtime.txt)

Done! Your public API is ready to use. 🎉

🛠 API Usage
GET / — Health Check
Returns:

json
Copy
Edit
{ "status": "InsightEdge API is running!" }
GET /headlines
Query Parameters:

Parameter	Type	Default	Description
limit	int	10	Max headlines per source
sources	string	all	Comma-separated: yahoo,google,et,cnbc

Example:

bash
Copy
Edit
/headlines?limit=5&sources=yahoo,google
Sample Response:

json
Copy
Edit
[
  {
    "source": "yahoo",
    "headlines": [
      {
        "title": "Market rallies after Fed comments",
        "sentiment": "positive",
        "score": 0.78
      }
    ]
  }
]
🧠 Sentiment Logic
score > 0.05: positive

score < -0.05: negative

Otherwise: neutral

Uses NLTK VADER or TextBlob in sentiment.py.

🐛 Troubleshooting
playwright.errors.BrowserError: Run playwright install

error: RPC failed on push: retry with stable internet

On Render: make sure port is set to 10000 in Start Command

📝 License
MIT © @ttanishh

🙋‍♂️ Author
Crafted with ❤️ by Tanish Panchal
GitHub: @ttanishh

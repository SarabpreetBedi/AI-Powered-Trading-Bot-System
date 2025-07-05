# 🤖 AI-Powered Trading Bot System

An intelligent crypto trading bot built with Python, Binance Testnet, TradingView Webhooks, and FastAPI. Uses AI signals like RSI, MACD, EMA crossovers, and more to make automated buy/sell decisions.

---

## 📁 Project Structure

![](images/Screenshot6.png) 

yaml
Copy
Edit

---

## 📸 Screenshots

| TradingView Alert | Webhook Server | Execution Log |
|------------------|----------------|---------------|
| ![](images/Screenshot1.png) | ![](images/Screenshot2.png) | ![](images/Screenshot3.png) |
![](images/Screenshot4.png) | ![](images/Screenshot5.png) |

---


## 🔐 Setup Binance & Webhook Credentials

### 1️⃣ Create a TradingView Webhook API Key

- Generate a UUID from [uuidgenerator.net](https://www.uuidgenerator.net/)
- Example:
  ```env
  API_KEY=tradingview_webhook_uk_bot
  SECRET_KEY=d4f0c532-3905-449f-b7da-69ee07125da7
2️⃣ Get Binance Testnet Keys
Go to Binance Testnet

Log in with your Binance account

Generate a new API Key and Secret

Add to your .env:

env
Copy
Edit
BINANCE_API_KEY=your_testnet_api_key
BINANCE_API_SECRET=your_testnet_api_secret
USE_TESTNET=true
⚙️ Example .env File
env
Copy
Edit
# Webhook Auth
API_KEY=tradingview_webhook_uk_bot
SECRET_KEY=d4f0c532-3905-449f-b7da-69ee07125da7

# Binance Testnet Keys
BINANCE_API_KEY=3Mq4UvD1ObhsGFVphr9hi4zv5dFxZ6GIWT64G41E0X6aNXwNEnPM0NCHSV3MU8Wq
BINANCE_API_SECRET=1cLewWfB6mxy98lda7gDVlt4ytW1n7uppebEjfpCbdZg149EaaEiqY6iPtPFcvXo
USE_TESTNET=true

# Binance Testnet Supported Symbols
# BNBUSDT, BTCUSDT, ETHUSDT, LTCUSDT, TRXUSDT, XRPUSDT, USDT, BUSD

# Trade Symbols
SYMBOLS=BNBUSDT,BTCUSDT,ETHUSDT

# Global Defaults
MAX_POSITION_SIZE=0.01
COOLDOWN_SECONDS=60

# Per-symbol Overrides (optional)
MAX_POSITION_SIZE_BNB=0.1
MAX_POSITION_SIZE_ETH=0.02
MAX_POSITION_SIZE_BTC=0.005
🧪 Run Locally (Virtual Environment)
1. Clone the Repository
bash
Copy
Edit
git clone https://github.com/SarabpreetBedi/AI-Powered-Trading-Bot-System.git
cd AI-Powered-Trading-Bot-System
2. Setup Virtual Environment
bash
Copy
Edit
python -m venv venv
# Windows:
venv\Scripts\activate

# macOS/Linux:
source venv/bin/activate

3. Install Dependencies
bash
Copy
Edit
pip install -r requirements.txt
4. Configure Environment
bash
Copy
Edit
cp .env.example .env
# Then edit .env with your API keys and symbols
5. Start Webhook Server
bash
Copy
Edit
uvicorn webhook_server.main:app --reload --port 8000
6. Test Signal Handling
bash
Copy
Edit
python -m trading_bot.main
🐳 Run with Docker
1. Build & Start Containers
bash
Copy
Edit
docker-compose up --build
2. Access FastAPI Docs
bash
Copy
Edit
http://localhost:8000/docs
3. Manually Trigger a Webhook
bash
Copy
Edit
curl -X POST http://localhost:8000/webhook \
  -H "Content-Type: application/json" \
  -d '{"symbol": "BTCUSDT", "rsi": 30, "macd": -0.1, "side": "buy"}'
📡 Connect with TradingView
1. Use the Provided Pine Script
strategy.pine contains AI-friendly logic for EMA/RSI/MACD/etc. At signal, it sends:

json
Copy
Edit
{
  "api_key": "tradingview_webhook_uk_bot",
  "symbol": "BTCUSDT",
  "price": "29150.12",
  "side": "buy",
  "rsi": "28.3",
  "macd": "-0.01"
}
⚠️ Ensure your TradingView alert() payload includes "symbol"!

2. Set Webhook URL
Use your server's public IP:

arduino
Copy
Edit
http://<your-ip>:8000/webhook
TradingView Settings	Webhook Example

✅ Features
🔎 AI-powered signal filtering

📉 Binance Testnet integration

🔄 Per-symbol position sizing

⏱ Cooldown logic

🧾 Trade logging to SQLite

🚀 FastAPI webhook receiver

🐳 Docker support

🧪 Run Unit Tests
bash
Copy
Edit
pytest tests/
⚠️ Disclaimer
This bot runs on Binance Testnet. It is for educational and testing purposes only. Use at your own risk and never with real funds unless you understand the risks involved.

📝 License
MIT License — free for personal or commercial use.

👨‍💻 Author
Sarabpreet Bedi

go
Copy
Edit

> ✅ **Place this `README.md` file at the root of your repository** and make sure the `images/` folder contains the referenced screenshots.

Would you like me to generate a `.env.example` file, `Dockerfile`, or `strategy.pine` to go along with it?

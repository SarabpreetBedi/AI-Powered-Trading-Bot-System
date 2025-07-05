# 🤖 AI-Powered Trading Bot System

An intelligent crypto trading bot built with Python, Binance Testnet, TradingView Webhooks, and FastAPI. Uses AI signals like RSI, MACD, EMA crossovers, and more to make automated buy/sell decisions.

---

## 📁 Project Structure

![](images/Screenshot6.png)

---

## 📸 Screenshots

| 📈 TradingView              | ⚙️ Webhook Server         | ✅ Trade Log              |
|----------------------------|---------------------------|---------------------------|
| ![](images/Screenshot1.png) | ![](images/Screenshot2.png) | ![](images/Screenshot3.png) |
| ![](images/Screenshot4.png) | ![](images/Screenshot5.png) |

---

## 🔐 API Keys & Setup

### 🔑 1. TradingView Webhook API Key

Generate from [uuidgenerator.net](https://www.uuidgenerator.net)

```env
API_KEY=tradingview_webhook_uk_bot
SECRET_KEY=d4f0c532-3905-449f-b7da-69ee07125da7
🔑 2. Binance Testnet Keys
Create from https://testnet.binance.vision

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
API_KEY=tradingview_webhook_uk_bot
SECRET_KEY=d4f0c532-3905-449f-b7da-69ee07125da7

BINANCE_API_KEY=3Mq4UvD1ObhsGFVphr9hi4zv5dFxZ6GIWT64G41E0X6aNXwNEnPM0NCHSV3MU8Wq
BINANCE_API_SECRET=1cLewWfB6mxy98lda7gDVlt4ytW1n7uppebEjfpCbdZg149EaaEiqY6iPtPFcvXo
USE_TESTNET=true

SYMBOLS=BNBUSDT,BTCUSDT,ETHUSDT

MAX_POSITION_SIZE=0.01
COOLDOWN_SECONDS=60

MAX_POSITION_SIZE_BNB=0.1
MAX_POSITION_SIZE_ETH=0.02
MAX_POSITION_SIZE_BTC=0.005
🧪 Run Locally (Virtual Environment)
1️⃣ Clone the Repo
bash
Copy
Edit
git clone https://github.com/SarabpreetBedi/AI-Powered-Trading-Bot-System.git
cd AI-Powered-Trading-Bot-System
2️⃣ Setup Virtual Environment
bash
Copy
Edit
python -m venv venv
Activate (choose your OS):

bash
Copy
Edit
venv\Scripts\activate
bash
Copy
Edit
source venv/bin/activate
3️⃣ Install Dependencies
bash
Copy
Edit
pip install -r requirements.txt
4️⃣ Create .env File
bash
Copy
Edit
cp .env.example .env
Edit .env with your API keys.

5️⃣ Start Webhook Server
bash
Copy
Edit
uvicorn webhook_server.main:app --reload --port 8000
6️⃣ Test Signal Manually
bash
Copy
Edit
python -m trading_bot.main
🐳 Run via Docker
1️⃣ Build and Start
bash
Copy
Edit
docker-compose up --build
2️⃣ Access API Docs
Visit:

bash
Copy
Edit
http://localhost:8000/docs
3️⃣ Test Webhook Manually
bash
Copy
Edit
curl -X POST http://localhost:8000/webhook \
  -H "Content-Type: application/json" \
  -d '{"symbol": "BTCUSDT", "rsi": 30, "macd": -0.1, "side": "buy"}'
📡 Connect to TradingView
✅ Example Pine Script Alert Payload
pinescript
Copy
Edit
alert('{' +
  '"api_key": "tradingview_webhook_uk_bot",' +
  '"symbol": "' + syminfo.ticker + '",' +
  '"price": "' + str.tostring(close) + '",' +
  '"side": "buy",' +
  '"rsi": "' + str.tostring(rsi) + '",' +
  '"macd": "' + str.tostring(macdLine) + '"' +
'}', freq=alert.freq_once_per_bar)
🔗 Webhook URL
text
Copy
Edit
http://<your-server-ip>:8000/webhook
Ensure port 8000 is open if you're using a cloud VPS.

✅ Features
🤖 AI-based decision making (RSI, MACD, EMA crossover)

🧠 LSTM & rule-based logic

🔄 Symbol-specific trade sizing

⏳ Cooldown management per symbol

🧾 Trade logging to SQLite

⚡ FastAPI webhook endpoint

🐳 Docker & virtual environment support

🧪 Run Unit Tests
bash
Copy
Edit
pytest tests/
⚠️ Disclaimer
This bot operates on Binance Testnet only.
It is meant for educational/testing purposes — do not use real funds unless you're fully aware of the risks.

📝 License
MIT License

👨‍💻 Author
Sarabpreet Bedi

retrogame-alert-bot/
├── main.py
├── search_engines/
│   ├── vinted.py
│   ├── marktplaats.py
│   └── tweedehands.py
├── telegram_bot.py
├── config.py
├── requirements.txt
└── README.md
from telegram_bot import send_alert
from search_engines.vinted import check_vinted
from search_engines.marktplaats import check_marktplaats
from search_engines.tweedehands import check_tweedehands

def run_all():
    results = []
    results += check_vinted()
    results += check_marktplaats()
    results += check_tweedehands()

    for item in results:
        send_alert(item)

if __name__ == "__main__":
    run_all()
   def check_vinted():
    return [{
        "platform": "Vinted",
        "title": "Nintendo DS met 3 games",
        "price": "35 EUR",
        "link": "https://www.vinted.be/item/xxx",
        "location": "Antwerpen",
        "datetime": "2025-06-29 15:23",
        "comparison": "-40% onder marktprijs"
    }]
    import requests
from config import TELEGRAM_BOT_TOKEN, TELEGRAM_CHAT_ID

def send_alert(item):
    msg = (
        f"🕹️ Nieuw zoekertje op {item['platform']}\n"
        f"📌 {item['title']}\n"
        f"💰 {item['price']}\n"
        f"📍 {item['location']}\n"
        f"📆 {item['datetime']}\n"
        f"📉 {item['comparison']}\n"
        f"🔗 {item['link']}"
    )

    url = f"https://api.telegram.org/bot{TELEGRAM_BOT_TOKEN}/sendMessage"
    data = {"chat_id": TELEGRAM_CHAT_ID, "text": msg}
    requests.post(url, data=data)
    TELEGRAM_BOT_TOKEN = "8192534864:AAG-ijCAa8n0eU5DYQ89qcgtatI-yF2R_bw"
TELEGRAM_CHAT_ID = "7628214873"
requests
# Retrogame Alert Bot

Deze bot controleert Vinted, Marktplaats en 2dehands op goedkope retro games & consoles en stuurt meldingen via Telegram.

## Gebruik

1. Vul je Telegram-bot token en chat ID in `config.py`
2. Run `main.py`
3. Ontvang meldingen rechtstreeks in je Telegram
4. 

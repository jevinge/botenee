pip install tweepy python-telegram-bot

import tweepy
import telegram
import time

# Configuración de la API de X (Twitter)
TWITTER_API_KEY = "f1lPGs051kG4HKJ2SAXAh0azK"
TWITTER_API_SECRET = "lXOpxdqW9nMVDeqiJsoZG83DmSQZiORLUZcLBO8cSuk15ncyo7"
TWITTER_ACCESS_TOKEN = "1878582226193121280-kTuYTeCY6Xb2BDNnZoNDgsy9BggsVC"
TWITTER_ACCESS_SECRET = "qSsP7R2EyVJbqOFXLBrKmAEUNglqaqy5ttDeCTLMpxX38"

# Configuración del bot de Telegram
TELEGRAM_BOT_TOKEN = "8002949345:AAGfWSMKQDZgL7YXjuC2hzcM-x0fjyMgZj4"
TELEGRAM_CHAT_ID = "7149515380"  # Puede ser el ID del grupo o usuario

# Autenticación con la API de X (Twitter)
auth = tweepy.OAuthHandler(TWITTER_API_KEY, TWITTER_API_SECRET)
auth.set_access_token(TWITTER_ACCESS_TOKEN, TWITTER_ACCESS_SECRET)
api = tweepy.API(auth)

# Configuración del bot de Telegram
bot = telegram.Bot(token=TELEGRAM_BOT_TOKEN)

# Usuario de Twitter a monitorear
USERNAME = "EneeHnOficial"
last_tweet_id = None

def obtener_ultimo_tweet():
    global last_tweet_id
    tweets = api.user_timeline(screen_name=USERNAME, count=1, tweet_mode="extended")
    if tweets:
        tweet = tweets[0]
        if last_tweet_id != tweet.id:
            last_tweet_id = tweet.id
            mensaje = f"Nuevo tweet de {USERNAME}: {tweet.full_text}\nhttps://twitter.com/{USERNAME}/status/{tweet.id}"
            bot.send_message(chat_id=TELEGRAM_CHAT_ID, text=mensaje)

while True:
    obtener_ultimo_tweet()
    time.sleep(60)  # Verifica cada minuto

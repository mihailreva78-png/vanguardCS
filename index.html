import threading
from telegram import InlineKeyboardButton, InlineKeyboardMarkup, Update
from telegram.ext import Updater, CommandHandler, CallbackContext

TOKEN = '8613337382:AAFwFxLpIvvkCfBTYECszdLvvMy0DVkzAL0'  # ваш токен

# Словарь для хранения данных пользователей
# {user_id: {'invites': int, 'ref_sent': bool, 'timer': Timer}}
user_data = {}

def send_ref_link(bot, user_id):
    """Отправляет реферальную ссылку через 60 секунд."""
    if user_id in user_data and not user_data[user_id].get('ref_sent', False):
        bot_username = bot.get_me().username
        ref_link = f"https://t.me/{bot_username}?start=ref{user_id}"
        bot.send_message(
            chat_id=user_id,
            text=f"Ваша реферальная ссылка:\n{ref_link}\nПригласите 2-х человек, и вы получите доступ к рассылке."
        )
        user_data[user_id]['ref_sent'] = True
        user_data[user_id]['timer'] = None

def start(update: Update, context: CallbackContext):
    user_id = update.effective_user.id
    text = update.message.text

    # Обработка перехода по реферальной ссылке
    if text.startswith('/start ref'):
        parts = text.split()
        if len(parts) > 1 and parts[1].startswith('ref'):
            try:
                ref_id = int(parts[1][3:])  # извлекаем ID пригласившего
                if ref_id != user_id and ref_id in user_data:
                    user_data[ref_id]['invites'] += 1
                    if user_data[ref_id]['invites'] >= 2:
                        context.bot.send_message(
                            chat_id=ref_id,
                            text="Оплата 10 звезд"
                        )
            except ValueError:
                pass
        update.message.reply_text("Добро пожаловать! Вы были приглашены.")
        return

    # Обычный запуск /start
    if user_id not in user_data:
        user_data[user_id] = {'invites': 0, 'ref_sent': False, 'timer': None}

    # Кнопки с каналами
    keyboard = [
        [InlineKeyboardButton("Канал 1", url="https://t.me/+R5PzyMESgYoyOTJl")],
        [InlineKeyboardButton("Канал 2", url="https://t.me/+DAgYl6xqvbJhYTE1")]
    ]
    reply_markup = InlineKeyboardMarkup(keyboard)
    update.message.reply_text(
        "Добро пожаловать! Подпишитесь на наши каналы:",
        reply_markup=reply_markup
    )

    # Запускаем таймер на 1 минуту, если ссылка ещё не была отправлена
    if not user_data[user_id].get('ref_sent', False):
        # Отменяем старый таймер, если есть
        old_timer = user_data[user_id].get('timer')
        if old_timer:
            old_timer.cancel()
        # Создаём новый
        timer = threading.Timer(60.0, send_ref_link, args=[context.bot, user_id])
        timer.daemon = True
        timer.start()
        user_data[user_id]['timer'] = timer

def main():
    updater = Updater(TOKEN, use_context=True)
    dp = updater.dispatcher
    dp.add_handler(CommandHandler("start", start))
    updater.start_polling()
    updater.idle()

if __name__ == '__main__':
    main()

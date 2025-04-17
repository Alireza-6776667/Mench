# mench 
from telegram.ext import ApplicationBuilder, CommandHandler, MessageHandler, filters

# توکن رباتت رو اینجا بذار
TOKEN = "7557864040:AAGGP_2WrarO7E5HOtkGz3dW7ML6ozKDF0g"

async def start(update, context):
    await update.message.reply_text("سلام! به ربات من خوش اومدی.")

async def handle_message(update, context):
    text = update.message.text.lower()
    if text == "استارت":
        await update.message.reply_text("بازی شروع شد!")
    elif text == "پایان بازی":
        await update.message.reply_text("بازی تموم شد!")
    else:
        await update.message.reply_text("متوجه نشدم چی گفتی!")

app = ApplicationBuilder().token(TOKEN).build()

app.add_handler(CommandHandler("start", start))
app.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, handle_message))

app.run_polling()

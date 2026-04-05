from telegram import Update, InlineKeyboardButton, InlineKeyboardMarkup
from telegram.ext import ApplicationBuilder, CommandHandler, CallbackQueryHandler, ContextTypes

# Start Menu
async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    keyboard = [
        [InlineKeyboardButton("📥 Install Git", callback_data="install")],
        [InlineKeyboardButton("⚙️ Setup Git", callback_data="setup")],
        [InlineKeyboardButton("🔗 Connect GitHub", callback_data="github")]
    ]

    reply_markup = InlineKeyboardMarkup(keyboard)

    await update.message.reply_text(
        "👋 Welcome to Git Tutor Bot!\n\nChoose a topic:",
        reply_markup=reply_markup
    )

# Handle button clicks
async def button(update: Update, context: ContextTypes.DEFAULT_TYPE):
    query = update.callback_query
    await query.answer()

    # Back button
    back_button = InlineKeyboardMarkup([
        [InlineKeyboardButton("🔙 Back to Menu", callback_data="menu")]
    ])

    if query.data == "install":
        await query.message.reply_text(
            "📥 *Install Git*\n\n"
            "1. Go to: https://git-scm.com/downloads\n"
            "2. Download and install\n"
            "3. Check:\ngit --version\n\n"
            "🎥 Watch video below:",
            parse_mode="Markdown"
        )

        await query.message.reply_video(
            video="https://www.youtube.com/watch?v=SWYqp7iY_Tc"
        )

        await query.message.reply_text("Choose next:", reply_markup=back_button)

    elif query.data == "setup":
        await query.message.reply_text(
            "⚙️ *Setup Git*\n\n"
            "git config --global user.name \"Your Name\"\n"
            "git config --global user.email \"your@email.com\"\n\n"
            "Check:\ngit config --list\n\n"
            "🎥 Watch video below:",
            parse_mode="Markdown"
        )

        await query.message.reply_video(
            video="https://www.youtube.com/watch?v=HkdAHXoRtos"
        )

        await query.message.reply_text("Choose next:", reply_markup=back_button)

    elif query.data == "github":
        await query.message.reply_text(
            "🔗 *Connect GitHub*\n\n"
            "1. Create account at https://github.com\n"
            "2. Generate SSH key:\n"
            "ssh-keygen -t ed25519 -C \"your@email.com\"\n"
            "3. Add key to GitHub\n"
            "4. Test:\nssh -T git@github.com\n\n"
            "🎥 Watch video below:",
            parse_mode="Markdown"
        )

        await query.message.reply_video(
            video="https://www.youtube.com/watch?v=RGOj5yH7evk"
        )

        await query.message.reply_text("Choose next:", reply_markup=back_button)

    elif query.data == "menu":
        keyboard = [
            [InlineKeyboardButton("📥 Install Git", callback_data="install")],
            [InlineKeyboardButton("⚙️ Setup Git", callback_data="setup")],
            [InlineKeyboardButton("🔗 Connect GitHub", callback_data="github")]
        ]

        reply_markup = InlineKeyboardMarkup(keyboard)

        await query.message.reply_text(
            "📋 Main Menu:",
            reply_markup=reply_markup
        )

# Run bot
app = ApplicationBuilder().token("8633654937:AAFrBff2T-ri2OK5Aln7knDGqNVcw_8hsHY").build()

app.add_handler(CommandHandler("start", start))
app.add_handler(CallbackQueryHandler(button))

app.run_polling()

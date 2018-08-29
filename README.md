       private static Telegram.Bot.TelegramBotClient bot;
       
       
       private void button1_Click(object sender, EventArgs e)
        {
            bot = new Telegram.Bot.TelegramBotClient("569317449:AAFJA9fJDirG3nEP15hrcx3i6BuoD6Xndb4");
            bot.OnMessage += BotOnMessageRecieved;
            bot.StartReceiving(new UpdateType[] { UpdateType.Message });
            button1.Enabled = false;

        }

        private static async void BotOnMessageRecieved(object sender, MessageEventArgs messageEventArgs)
        {
            Telegram.Bot.Types.Message msg = messageEventArgs.Message;
            if (msg == null || msg.Type != MessageType.Text) return;

            string answer = "";

            switch (msg.Text)
            {
                case "/start":
                    answer = "напиши любовь";
                    break;
                case "/любовь":
                    answer = "люблю тебя";
                    break;
                default:
                    answer = "http://zhzh.info/_bl/214/72118122.jpg";
                    break;
            }
            await bot.SendTextMessageAsync(msg.Chat.Id, answer);
        }

MarbineFX Unified Dashboard V1

- index.html is the only page users navigate.
- Top-right page links are removed.
- ENGLISH / MALAY is centered at the top.
- All navigation is in CHOOSE YOUR SECTION.
- Home / Indicators / Study Pairs / Signal Lab / Forum load below without leaving index.html.
- The embedded Home hides the old View More button.

For accurate live TP/SL/Entry:
- signal.html now calls a Supabase Edge Function named market-signal.
- market-signal calculates from the same live OHLC candles used to draw the chart.
- It will NOT invent price levels if live market data is unavailable.
- Add the secret TWELVE_DATA_API_KEY in Supabase, then deploy supabase-edge-function-market-signal/index.ts.

Trade types:
- Short Trade: 15-minute candles, review in about 2–4 hours.
- Day Trade: 1-hour candles, review before the trading day ends.
- Swing Trade: 4-hour candles, review in about 3–5 trading days.

Telegram:
Yes, automatic Telegram channel signals are possible. Telegram's Bot API supports sending channel messages with sendMessage.
Never put the bot token in HTML. Store TELEGRAM_BOT_TOKEN and TELEGRAM_CHAT_ID as server-side Supabase secrets.
The included telegram-signal Edge Function is the secure sender.
For automatic signals even when nobody has the website open, schedule a Supabase Cron job to scan the markets and call the sender when a new qualified signal appears.

Signals cannot be guaranteed accurate. Use confidence thresholds and deduplication before broadcasting.

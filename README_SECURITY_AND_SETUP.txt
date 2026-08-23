MARBINEFX PUBLIC AUTH + SIGNAL V2

SECURE AUTH
- index.html is now the login gate.
- Email/password signup and login use Supabase Auth.
- Google login button is included; enable Google provider in Supabase Auth before it works.
- Forgot password sends a reset LINK. Passwords are never emailed or revealed.
- app.html checks for a valid Supabase session before showing the dashboard.

IMPORTANT OWNER SETUP
- Do NOT hard-code owner username/password marbine/marbine in public HTML. Anyone can read public HTML.
- Use a normal Supabase account for the owner and enforce owner-only Telegram sending server-side.
- Recommended owner identity: your private owner email stored as a Supabase Edge Function secret OWNER_EMAIL.

SIGNAL ROOM CHANGES TO IMPLEMENT/DEPLOY
- Remove account balance and risk percentage fields.
- If forex market is closed, show MARKET CLOSED and no Entry/SL/TP.
- Pair selection refreshes the chart.
- Add chart timeframe selector (5m/15m/30m/1h/4h).
- Best-setup filter should require active session, adequate volatility/liquidity, directional agreement, and a confirmed liquidity sweep/reclaim before showing BUY/SELL. Otherwise show WAIT / NO HIGH-QUALITY SETUP.
- Do not claim a win rate until the exact strategy is backtested on historical data. Show 'Win rate: not verified' or a separately calculated backtest statistic.
- Public users must never auto-post to Telegram. Owner-only Send to Telegram must be enforced by the Edge Function, not only by hiding the button.

TELEGRAM MESSAGE
Pair / timeframe / BUY-SELL / Entry / TP1-3 / SL / session / volatility / liquidity sweep / indicators used / setup score / verified historical win rate (only after backtest).

NOTE
The currently deployed market-signal function may still contain the earlier automatic Telegram call. Replace it with a no-auto-send version before public launch.

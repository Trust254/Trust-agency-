# TradePilot AI

Live deployment: https://tradepilot-ai-4q8e.onrender.com

A mobile-first trading terminal deployed on Render and backed by a dedicated Supabase project.

## Included
- Supabase email/password authentication.
- User-owned watchlists with row-level security.
- Live public Binance candle feed for BTC, ETH, SOL and BNB (refreshes every 60 seconds).
- Transparent EMA(9/21), RSI(14), and momentum strategy signals.
- Context-aware rule-based assistant that explains signals and basic risk concepts.
- Paper trading with $10,000 virtual starting cash.
- Atomic database RPC for paper orders, including cash and position checks; direct client updates to balances and direct order inserts are blocked.
- PWA manifest, service worker and app icon for Android installation.

## Backend
- Supabase project: `tradepilot-ai`
- Project URL: `https://fdqxywntsvejokucfvcm.supabase.co`
- Project ref: `fdqxywntsvejokucfvcm`
- Public publishable key is configured in the frontend. Never put a Supabase service-role key in browser code.

## Important scope and safety
This deployed version is a working market-monitoring and paper-trading application. The strategy engine is deterministic technical analysis, not a trained predictive model or a connected generative AI model. The assistant is rule-based and does not call an LLM. The market feed currently covers selected crypto pairs only. It does not connect to a broker, route live orders, or handle deposits/withdrawals. No real-money trading is enabled. Do not represent signals as guaranteed or personalized financial advice.

To add a true generative AI assistant, configure a server-side model-provider API key as a secret in a secure backend/edge function. To enable real-money execution, integrate a regulated broker API with account authorization, order validation, audit logs, jurisdiction checks and risk limits. Never expose provider or broker secrets in this frontend.

## Run locally
Serve this directory over HTTP, for example:

```bash
python3 -m http.server 8080
```

Open `http://localhost:8080`.

## Install on Android
Open the live URL in Chrome, open the three-dot menu, then choose **Install app** or **Add to Home screen**.

## Deployment source
The Render static site deploys from branch `tradepilot-ai-deploy`. The repository's original `main` branch was not changed.
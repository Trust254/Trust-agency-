# TradePilot AI

A mobile-first trading terminal MVP with Supabase authentication, per-user watchlists, virtual paper orders, a transparent technical-indicator strategy engine, and PWA installation support.

## Current functionality
- Supabase email/password sign-up and sign-in.
- User-owned watchlists and paper-trading records protected by Row Level Security.
- Public Binance hourly candle feed for BTC, ETH, SOL and BNB.
- Explainable EMA(9/21), RSI(14), and momentum signal (BUY/SELL/HOLD).
- Assistant chat explains the currently computed signal and basic risk concepts.
- Paper orders only. No real-money execution or broker connectivity.
- PWA manifest, service worker and app icon.

## Configuration
The frontend uses the public Supabase publishable key. It is safe to include in browser code when RLS is enabled. Never add a Supabase service-role/secret key to this repository.

Project URL: `https://fdqxywntsvejokucfvcm.supabase.co`

Publishable key is already configured in `index.html`.

## Run locally
Serve this directory over HTTP (not `file://`), for example:

```bash
python3 -m http.server 8080
```

Open `http://localhost:8080`.

## Deploy
Publish the repository as a Render Static Site with build command `echo "Static site ready"` and publish directory `.`. Connect the repository in Render, then deploy. After deployment, open the HTTPS URL in Chrome and choose **Install app** or **Add to Home screen**.

## Important limitations
The strategy engine is an explainable technical-indicator model, not a trained predictive AI model. The chat assistant currently uses local deterministic explanations; connect a secured server-side AI provider before advertising generative AI. Market feed availability depends on Binance API access in the visitor's region. Other asset classes and broker integrations are not connected yet. No live trading is enabled.

## Security
All public tables have RLS. User data policies scope access to `auth.uid()`. The `ai_signals` table is authenticated-read-only; only trusted backend/service-role processes should write signals. Never expose service credentials in browser code.
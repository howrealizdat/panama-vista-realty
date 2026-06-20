# 🏝️ Panama Vista Realty — AI Real Estate Concierge

A full-stack AI concierge for a Panama luxury-real-estate site: live property listings plus an AI agent with real working knowledge of Panama real estate, foreign-buyer law, residency/visa programs, and investment strategy. Every Claude API call is proxied through a Netlify serverless function, so the API key is **never** exposed in the browser.

▶ **Live demo:** https://luxury-tartufo-ffc74b.netlify.app *(password-gated — access code available on request)*

> 🍔 **Same architecture, different industry:** this secure serverless AI-concierge pattern also powers [Detroit's Finest Burgers](https://detroits-finest-burgers.netlify.app), a restaurant concierge — proof the approach transfers cleanly across domains. *(Demo access on request.)*

## Architecture highlights

- **Secure key handling.** All Anthropic API calls route through a Netlify serverless function (`netlify/functions/chat.js`) that injects the key from a server-side environment variable (`process.env.ANTHROPIC_API_KEY`). The key never appears in client-side source. A redirect maps `/api/chat` → the function.
- **No framework, no build step.** The entire front end is a single `index.html` (HTML/CSS/JS).
- **Domain-grounded agent.** A system prompt gives the assistant genuine working knowledge of Panama property, foreign-buyer law, visa/residency programs, and investment considerations — not a generic chatbot.
- **Access gate.** A lightweight client-side passcode screen controls who reaches the demo. *(The code in this repo uses a placeholder, `CORRECT_PASSWORD`; the live demo's real code is shared on request.)*

## Project layout

- `index.html` — the full front end: property listings UI, the AI concierge chat, and the access gate.
- `netlify/functions/chat.js` — serverless proxy that calls the Anthropic API using the server-side key.
- `netlify.toml` — Netlify build + redirect config (`/api/chat` → the function).

## Run it yourself

1. Add an `ANTHROPIC_API_KEY` environment variable in your Netlify site settings.
2. Deploy this folder to Netlify (the functions directory is set in `netlify.toml`).
3. Set your own access code in `index.html` (`CORRECT_PASSWORD`).

> The API key is supplied via an environment variable and is never committed to this repository. The client-side passcode is a simple access screen, not a security boundary — protect the live endpoint with a usage/spend cap.

---

Built by **Edmund Gray**.

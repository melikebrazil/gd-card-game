# Geometry Dash: Level Collectors

A fan-made level-card collecting and trading website built with HTML, CSS, JavaScript, and Supabase.

## Features
- Email/password accounts and player usernames
- 500 starting coins and 100-coin mystery packs
- Server-side rarity odds: Common 60%, Uncommon 25%, Rare 10%, Legendary 4%, Mythic 1%
- Player inventory and collection dex
- Online player directory and card-for-card trading
- Cards are locked while offered in an open trade
- Supabase Row Level Security and Realtime trade updates

## Run locally
Serve this folder with a local web server, for example:
```bash
python -m http.server 8000
```
Then open http://localhost:8000.

## Deploy
Deploy as a static site with GitHub Pages, Netlify, or Vercel. No build step is required.

## Supabase
The browser uses only the Supabase publishable key. Never put a service-role or secret key in frontend code. The database tables, RLS policies, signup trigger, and pack/trade RPC functions are configured in the connected project.

## Screenshots
The catalog supports a screenshot_url field. Until permitted screenshots are added, cards use CSS-generated artwork. Only add screenshots you own or have permission to use.

This is an independent fan project and is not affiliated with RobTop Games.

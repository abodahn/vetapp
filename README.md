# VetApp (Flask) — Vercel Deployment Pack

## What you get
- `app.py` (your app, patched to use a writable temp folder on Vercel)
- `requirements.txt` (Python dependencies)
- `vercel.json` (forces all routes to go to `app.py`)

## Important note about data (VERY IMPORTANT)
This app stores data in `.xlsx` files (owners, pets, bookings, etc).
On Vercel, the filesystem is **ephemeral**. Files written at runtime are **NOT guaranteed to persist**.
For production, move storage to a database (e.g., Vercel Postgres/KV, Supabase, etc).

## Deploy steps (GitHub)
1. Create a GitHub repo and push these files.
2. Import the repo in Vercel Dashboard.
3. (Recommended) Add environment variables:
   - `VETAPP_SECRET_KEY` = a long random string
   - optionally set `ADMIN_USER`, `ADMIN_PASS` if you changed them in code
4. Deploy.

## Deploy steps (Vercel CLI)
```bash
npm i -g vercel
vercel login
vercel deploy
```

## Local run (standard Flask)
```bash
python -m venv .venv
.venv\Scripts\activate   # Windows
pip install -r requirements.txt
python app.py
```

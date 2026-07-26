# SentiTrack AI

**A private, AI-powered journal that turns your daily reflections into mood insights, weekly summaries, and self-awareness.**

Write the way you already do in any journal. SentiTrack AI reads each entry and reflects patterns back to you — mood, sentiment, weekly recaps, and trends over time — so the slow shifts you'd normally miss become visible.

**Try it now:** **[sentitrackai.netlify.app](https://sentitrackai.netlify.app/)**

No install required — open the link, create a free account, and start journaling.

---

## What is it?

SentiTrack AI isn't a mood tracker you fill in manually, and it isn't a generic notes app. The *writing itself* is the input — you journal normally, and AI does the noticing:

- **Sentiment analysis** — every entry gets a mood, emotion, sentiment, and confidence score
- **Weekly summaries** — a short AI-written recap of your week, with gentle suggestions
- **Dashboard** — streaks, sentiment trends, and your most common moods and emotions
- **Insights** — AI-noticed patterns across your journaling history (e.g. *"your mood trends more positive after exercise"*)
- **Search** — find past entries by keyword, date, mood, emotion, or sentiment

**Privacy:** every entry, analysis, and insight is scoped to your account behind authentication. Nothing is shared between users, and the raw AI response is never stored — only the structured result (sentiment, mood, emotion, confidence).

---

## How to use it

1. **Open the app** → [sentitrackai.netlify.app](https://sentitrackai.netlify.app/)
2. **Create an account** and log in (sessions stay active via automatic token refresh).
3. **Write a journal entry** — just write, the same as any private journal.
4. **Analyze it** — run AI sentiment analysis on the entry to see its mood, emotion, sentiment, and confidence.
5. **Check your Dashboard** — see totals, streaks, sentiment breakdown, and trend charts as entries build up.
6. **Generate a Weekly Summary** — get an AI recap of any week with suggestions.
7. **Generate Insights** — ask the AI to surface patterns across your whole history.
8. **Search** — filter past entries by keyword, date range, mood, emotion, or sentiment.

> AI calls (analysis, summaries, insights) can take a few seconds — the app shows a loading state while it works.

---

## Project structure

This repository contains both halves of the product:

```text
SentiTrack/            # Backend — FastAPI REST API, AI sentiment analysis, auth, database
SentiTrackAiFrontend/  # Frontend — React + TypeScript web app (deployed at sentitrackai.netlify.app)
```

Each has its own detailed README:

- [`SentiTrack/README.md`](SentiTrack/README.md) — backend setup, API reference, deployment
- [`SentiTrackAiFrontend/README.md`](SentiTrackAiFrontend/README.md) — frontend setup, scripts, environment variables

## Tech stack

| Layer | Technology |
| --- | --- |
| Frontend | React 19, Vite, TypeScript, Tailwind CSS, Framer Motion |
| Backend | FastAPI, SQLAlchemy 2.0 + Alembic, PostgreSQL/SQLite, JWT auth |
| AI | OpenRouter LLMs (sentiment, summaries, insights) |
| Hosting | Netlify (frontend), Render (backend) |

## Running it yourself

The live demo requires no setup, but if you want to self-host or develop locally, you'll need both the backend and frontend running (the frontend calls the backend for everything):

```bash
# 1. Backend
cd SentiTrack
python -m venv .venv && .venv\Scripts\Activate.ps1   # Windows
pip install -r requirements.txt
cp .env.example .env    # set JWT_SECRET_KEY and OPENROUTER_API_KEY
alembic upgrade head
uvicorn app.main:app --reload

# 2. Frontend (in a new terminal)
cd SentiTrackAiFrontend
npm install
cp .env.example .env    # set VITE_API_ROOT_URL to the backend URL above
npm run dev
```

Full setup, configuration, and deployment details are in each subfolder's README linked above.

## Project status

All core areas are implemented end-to-end: authentication, journaling, AI sentiment analysis, the analytics dashboard, weekly summaries, search, and insights. Ongoing work includes background processing, caching, automated tests, and further production hardening — see [`SentiTrack/requirement.md`](SentiTrack/requirement.md) for details.

## Contributing

This is currently a solo project and not yet set up for external contributions, but issues and suggestions are welcome.

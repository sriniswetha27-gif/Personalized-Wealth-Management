# Personalized Wealth Management & Goal Tracker

Full-stack prototype for goal-based investing, portfolio tracking, simulations, recommendations, and live market data.

## Stack

- React, Vite, TypeScript, Tailwind CSS, Recharts
- FastAPI, SQLAlchemy, PostgreSQL, JWT auth
- Alpha Vantage quote API with Yahoo Finance fallback
- Celery and Redis scaffold for scheduled market refresh jobs

## Run From Scratch

1. Start PostgreSQL and Redis:

```bash
docker compose up -d
```

2. Configure backend:

```bash
cd backend
copy .env.example .env
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```

3. Configure frontend:

```bash
cd frontend
copy .env.example .env
npm install
npm run dev
```

4. Open `http://localhost:5173`, register a user, add holdings and goals, then run forecasts.


## API Notes

- Auth: `POST /api/auth/register`, `POST /api/auth/login`, `GET /api/auth/me`
- Portfolio: `GET/POST /api/portfolio/holdings`, `GET /api/portfolio/summary`
- Goals: `GET/POST /api/goals`
- Market: `GET /api/market/quote/{symbol}`, `GET /api/market/history/{symbol}`
- Planning: `POST /api/planning/simulate`, `GET /api/planning/recommendations`

Set `ALPHA_VANTAGE_API_KEY` in `backend/.env` to use Alpha Vantage first. Without it, the backend uses Yahoo Finance.

# Finora

Finora is a personal finance management web app built with vanilla JavaScript, Express, and Supabase. It focuses on practical budgeting, elegant analytics, fast interaction, and deployment-ready structure for local development and Vercel.

## Features

- Email signup, login, and logout with Supabase Auth
- Income and expense tracking with search, filters, sort, and mobile swipe delete
- Monthly and category budgets with utilization rings and smart overspend alerts
- Premium dark dashboard with glassmorphism cards, animated counters, and lightweight interactions
- Analytics including category pie chart, income versus expense bars, monthly spending line chart, heatmap, activity sparkline, and health gauge
- Quick add transaction modal, bottom navigation, floating action button, and theme toggle

## Tech Stack

- Frontend: HTML5, CSS3, vanilla JavaScript, Chart.js
- Backend: Node.js, Express.js
- Database and Auth: Supabase PostgreSQL and Supabase Auth
- Deployment: Vercel

## Project Structure

```text
frontend/
backend/
database/
docs/
package.json
vercel.json
.env.example
```

## Installation Guide

1. Copy `.env.example` to `.env`
2. Fill in the Supabase values
3. Install dependencies:

```bash
npm install
```

4. Run the app locally:

```bash
npm run dev
```

5. Open `http://localhost:3000`

## Supabase Setup

1. Create a new Supabase project from the Supabase dashboard
2. Go to Project Settings → API
3. Copy:
   - Project URL
   - anon public key
   - service role key
4. Paste those values into `.env`
5. Open the SQL Editor in Supabase
6. Copy and run the contents of `database/schema.sql`
7. In Authentication → Providers, keep Email enabled
8. In Authentication → URL Configuration, add:
   - `http://localhost:3000`
   - your Vercel production URL

## Environment Variables

Use these values in `.env`:

```env
PORT=3000
APP_URL=http://localhost:3000
SUPABASE_URL=https://your-project-id.supabase.co
SUPABASE_ANON_KEY=your-supabase-anon-key
SUPABASE_SERVICE_ROLE_KEY=your-supabase-service-role-key
DEFAULT_CURRENCY=USD
```

## Local Development Notes

- The backend serves the frontend statically, so one command runs the entire app
- The frontend fetches the public Supabase configuration from `/api/config`
- All data APIs are protected by Supabase session validation, rate limiting, Helmet, CSRF checks, and payload validation

## Vercel Deployment

1. Import the repository into Vercel
2. Keep the root directory as the project root
3. Add all environment variables from `.env.example`
4. Deploy
5. Add the deployed URL to Supabase Authentication redirect settings

More deployment details are in `docs/deployment.md`.

## Future Improvements

- Recurring transactions and bill reminders
- CSV export and import
- Shared household budgets
- Goal-based savings plans
- Multi-currency reporting

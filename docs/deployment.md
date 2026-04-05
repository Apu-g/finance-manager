# Deployment Guide

## Local Run

```bash
npm install
npm run dev
```

The app runs on `http://localhost:3000`.

## Vercel Deployment

### 1. Project Import

- Create a new Vercel project
- Point it to this repository root
- Leave the default framework preset as Other

### 2. Environment Variables

Add these variables in Vercel Project Settings:

```env
PORT=3000
APP_URL=https://your-vercel-domain.vercel.app
SUPABASE_URL=https://your-project-id.supabase.co
SUPABASE_ANON_KEY=your-supabase-anon-key
SUPABASE_SERVICE_ROLE_KEY=your-supabase-service-role-key
DEFAULT_CURRENCY=USD
```

### 3. Supabase Configuration

- Add the Vercel production URL in Supabase Authentication redirect URLs
- Add the same URL in Supabase Site URL
- Run `database/schema.sql` if you have not already done that

### 4. Routing

`vercel.json` routes:

- `/api/*` to the Express backend
- `/` to `frontend/index.html`
- `/login`, `/signup`, `/dashboard` to their HTML files
- `/css/*`, `/js/*`, `/components/*` to static frontend assets

### 5. Production Check

After deployment verify:

- signup works
- login works
- dashboard loads analytics
- transactions can be created and deleted
- budgets save successfully

## Security Notes

- Never expose the service role key in frontend code
- Only the anon key is returned to the browser through `/api/config`
- Server routes validate the Supabase access token on every protected request
- CSRF protection is required for write actions

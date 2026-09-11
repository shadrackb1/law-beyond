# Law Beyond

<img src="./assets/header.svg" width="100%" alt="header" />


A productivity and social platform for law students â€” track streaks, manage study plans, monitor budgets, and connect with peers. Built with React, TypeScript, Tailwind CSS, Supabase, and M-Pesa payments.

## Features

- **Home Dashboard** â€” daily overview, quick actions, notifications
- **Streaks & Social Feed** â€” create posts, comment, like, build daily streaks
- **Study Planner** â€” manage tasks, assignments, and deadlines
- **Budget Tracker** â€” income/expense tracking, transaction history, spending charts
- **Push Notifications** â€” real-time web push alerts
- **Premium Subscriptions** â€” feature gating with M-Pesa STK Push payments
- **Auth** â€” email/password login and signup via Supabase
- **Responsive** â€” mobile bottom nav + desktop sidebar layouts

## Tech Stack

- **Frontend:** React 19, TypeScript 6, Vite 8, Tailwind CSS 4
- **Backend:** Supabase (Auth, PostgreSQL, Edge Functions in Deno)
- **Payments:** M-Pesa via Lipana API (STK Push)
- **Push Notifications:** Web push via Supabase Edge Functions
- **Error Tracking:** Sentry
- **Image Hosting:** Cloudinary

## Getting Started

### Prerequisites

- Node.js 18+
- A [Supabase](https://supabase.com) project
- A [Lipana](https://lipana.io) account (for M-Pesa)
- A [Sentry](https://sentry.io) project (optional)
- A [Cloudinary](https://cloudinary.com) account (optional)

### Install

```bash
npm install
cp .env.example .env
```

### Environment Variables

```env
VITE_SUPABASE_URL=your-project-url
VITE_SUPABASE_ANON_KEY=your-anon-key
VITE_SENTRY_DSN=your-sentry-dsn        # optional
VITE_CLOUDINARY_CLOUD_NAME=your-cloud  # optional
```

Get Supabase credentials from your [Supabase dashboard](https://supabase.com/dashboard) â†’ Project Settings â†’ API.

### Run

```bash
npm run dev
```

### Build

```bash
npm run build
```

## Project Structure

```
src/
â”œâ”€â”€ components/
â”‚   â”œâ”€â”€ layout/              # App shell components
â”‚   â”‚   â”œâ”€â”€ BottomNav.tsx
â”‚   â”‚   â”œâ”€â”€ DesktopSidebar.tsx
â”‚   â”‚   â””â”€â”€ NotificationsDropdown.tsx
â”‚   â””â”€â”€ ui/                  # Reusable UI components
â”œâ”€â”€ features/
â”‚   â”œâ”€â”€ auth/                # Auth.tsx â€” login & signup
â”‚   â”œâ”€â”€ dashboard/           # HomeDashboard
â”‚   â”œâ”€â”€ streaks/             # Streaks, StreakPost, PostDetail, CreatePostModal
â”‚   â”œâ”€â”€ planner/             # Planner â€” tasks & assignments
â”‚   â”œâ”€â”€ budget/              # BudgetTracker
â”‚   â”œâ”€â”€ profile/             # Profile
â”‚   â”œâ”€â”€ notifications/       # NotificationsPage
â”‚   â””â”€â”€ subscription/        # SubscriptionGate, PaymentPage
â”œâ”€â”€ contexts/
â”‚   â””â”€â”€ AuthContext.tsx       # Supabase auth provider
â”œâ”€â”€ hooks/                   # Custom React hooks
â”œâ”€â”€ lib/
â”‚   â”œâ”€â”€ api.ts               # API helpers
â”‚   â”œâ”€â”€ supabase.ts          # Supabase client init
â”‚   â”œâ”€â”€ cloudinary.ts        # Cloudinary upload config
â”‚   â”œâ”€â”€ notify.ts            # Push notification helpers
â”‚   â”œâ”€â”€ sentry.ts            # Sentry init
â”‚   â””â”€â”€ circuit-breaker.ts   # Circuit breaker for API calls
â”œâ”€â”€ App.tsx                  # Router + auth guards
â”œâ”€â”€ main.tsx                 # Entry point
â””â”€â”€ index.css                # Tailwind + design tokens

supabase/
â””â”€â”€ functions/               # Supabase Edge Functions (Deno)
    â”œâ”€â”€ initiate-payment/    # M-Pesa STK Push via Lipana
    â”œâ”€â”€ mpesa-webhook/       # M-Pesa payment callback
    â””â”€â”€ send-push/           # Web push notification sender
```

## Database

Supabase manages auth, database, and RLS policies. Tables include:

- `profiles` â€” user profiles (auto-created on signup)
- `posts` / `comments` / `likes` â€” social feed and streaks
- `tasks` / `assignments` â€” planner and coursework
- `transactions` â€” budget tracking
- `subscriptions` â€” premium tier management
- `notifications` â€” push notification records

Run migrations via the Supabase CLI or SQL Editor.

## Deployment

**Frontend:** Deploy to Vercel (auto-detects Vite):

```bash
npm run build
```

**Edge Functions:** Deploy via Supabase CLI:

```bash
supabase functions deploy
```

## License

MIT

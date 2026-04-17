# Farm2Market – No Middlemen, Better Income

## Overview

A full-stack agriculture marketplace platform where farmers sell crops directly to buyers, cutting out middlemen for better income. Production-grade with real data, AI price suggestions, live market prices, analytics dashboards, and role-based auth.

## Architecture

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9

## Stack

### Frontend (`artifacts/farm2market/`)
- React 18 + Vite + Tailwind CSS v4
- React Query (TanStack Query) for data fetching
- Wouter for routing
- Recharts for charts (price trends, demand breakdown, top crops)
- React Hook Form + Zod for forms
- next-themes for dark mode
- Framer Motion for animations

### Backend (`artifacts/api-server/`)
- Node.js + Express 5 (MVC)
- bcryptjs for password hashing
- jsonwebtoken (JWT) for auth
- Role-based access: farmer, buyer, admin

### Database (`lib/db/`)
- PostgreSQL + Drizzle ORM
- Tables: users, crops, market_prices, purchase_requests

### API Contract (`lib/api-spec/`)
- OpenAPI 3.1 spec → Orval codegen → React Query hooks

## Key Features

- JWT auth with role-based access (Farmer, Buyer, Admin)
- AI Price Suggestions (rule-based: demand, supply, location)
- Live Market Prices (auto-refresh every 5s)
- Analytics Dashboard with charts
- Buyer Dashboard with filters (crop type, location, price range)
- Farmer Dashboard with CRUD + AI suggestions
- Admin Panel
- "Run Demo" button to seed realistic data
- "Explain This Page" button on every page
- Dark mode toggle
- Download report (print)

## Demo Accounts (after running Demo)
- Farmer: rajesh.kumar@farm2market.com / demo1234
- Buyer: arjun.mehta@farm2market.com / demo1234

## Key Commands

- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes
- `pnpm --filter @workspace/api-server run dev` — run API server
- `pnpm --filter @workspace/farm2market run dev` — run frontend

## Routes

### Pages
- `/` — Home landing page
- `/login` — Login with role selection
- `/signup` — Registration
- `/farmer` — Farmer Dashboard (add/edit/delete crops)
- `/buyer` — Buyer Dashboard (browse, filter, request purchase)
- `/market` — Live Market Prices with charts
- `/analytics` — Analytics Dashboard
- `/admin` — Admin Panel
- `/about` — About & Tech explanation
- `/contact` — Contact form

### API Endpoints
- `/api/auth/signup`, `/api/auth/login`, `/api/auth/me`
- `/api/crops` (GET, POST), `/api/crops/:id` (GET, PUT, DELETE)
- `/api/crops/:id/ai-price` — AI price suggestion
- `/api/prices` — Live market prices
- `/api/prices/history` — Price history for charts
- `/api/analytics/dashboard`, `/api/analytics/crops-by-demand`, `/api/analytics/top-crops`, `/api/analytics/location-summary`
- `/api/purchases` (GET, POST), `/api/purchases/:id/status` (PUT)
- `/api/demo/run` — Seed demo data

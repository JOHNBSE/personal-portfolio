---
title: RentDesk / SystemV1
repo_url: https://github.com/JOHNBSE/SystemV1
image: /assets/images/SystemV1-placeholder.svg
excerpt: "RentDesk — a multi-tenant property management system (practice project)."
---

RentDesk is a Laravel REST API backing a property-management platform with three roles: **Admin** (platform-wide visibility), **Owner** (manages their own properties, units, tenants, payments, maintenance requests — fully isolated from other owners), and **Tenant** (sees only their own unit, payments, and messages).

> **Vibe-coded practice project.** Built almost entirely through AI-assisted prompts rather than hand-written engineering. It's a DevSecOps training ground for practicing security audits (broken authorization, insecure defaults, missing validation, etc.) — not production-ready as-is.

Two front ends talk to the same API: a zero-build vanilla JS SPA served directly by Laravel, and a separate Vite + React app for comparison.

## Architecture notes

- **Multi-tenancy**: row-level isolation via an `owner_id` column + an Eloquent global scope (`OwnerScope`), not schema-per-tenant.
- **AuthN**: Laravel Sanctum. Browser clients get an HttpOnly session cookie (CSRF-protected); API clients can use Sanctum personal access tokens.
- **AuthZ**: Laravel Policies per model, gating create/view/update/delete per role.
- **Suspension enforcement**: `EnsureActive` middleware blocks suspended owners mid-session, not just at login.

## Running it

```bash
composer install
cp .env.example .env
php artisan migrate --seed
php artisan serve --port=8000
```

Seeded accounts (password: `password`): admin@example.com, owner@example.com, tenant@example.com

**React UI** (optional):
```bash
cd frontend
npm install
npm run dev   # http://localhost:5173, proxies API calls to :8000
```

Source: https://github.com/JOHNBSE/SystemV1

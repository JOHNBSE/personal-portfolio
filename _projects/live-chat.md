---
title: Live Chat — v1.0
repo_url: https://github.com/JOHNBSE/live-chat
image: /assets/images/live-chat-placeholder.svg
excerpt: "A multi-tenant live chat platform (Laravel 12, React dashboard)."
---

A multi-tenant live chat platform. Admins register, create sites, and embed a lightweight JavaScript widget on any website. Visitors chat through the widget; admins respond via the React dashboard.

> v1.0 uses HTTP polling for real-time communication (widget polls every 1s, dashboard every 3s). v2.0 will replace polling with WebSockets.

## Tech Stack

| Layer | Technology | Version |
|-------|------------|---------|
| Backend | Laravel | 12.0 |
| PHP | PHP | 8.2+ |
| Authentication | Laravel Sanctum | 4.0 |
| Database | SQLite (development) | — |
| Admin Dashboard | React | 19.2 |
| HTTP Client | Axios | 1.16 |
| Build Tool | Vite | 7.0 |
| CSS Framework | Tailwind CSS | 4.0 |
| Widget | Vanilla JavaScript | — |

## How it works

1. An admin registers and logs in to the dashboard.
2. They create a **Site**, which generates a unique `site_key`.
3. They embed `widget.js` on their website, initialised with that `site_key`.
4. Visitors open the widget and start a conversation.
5. The admin sees the conversation appear in the dashboard and can reply in real time.

## Database Schema

```
User ──hasMany──> Site ──hasMany──> Visitor
                       └──hasMany──> Conversation ──hasMany──> Message
```

## API Overview

All endpoints are prefixed with `/api`.

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| POST | `/register` | — | Create admin account |
| POST | `/login` | — | Login, returns Bearer token |
| GET | `/sites` | Sanctum | List your sites |
| POST | `/sites` | Sanctum | Create a site |
| GET | `/admin/conversations` | Sanctum | List all conversations |
| POST | `/admin/message` | Sanctum | Send admin reply |
| POST | `/widget/conversation/start` | Site Key | Start a conversation |
| POST | `/widget/message` | Site Key | Send visitor message |

Widget routes authenticate via the `X-Site-Key` request header instead of a Bearer token.

## Security

- Rate limiting on auth routes (5 requests/minute)
- Throttle middleware on widget message sending to prevent spam
- CORS restricted to `localhost:3000` for dashboard routes; open for widget routes
- Security headers applied globally via middleware

## Running it

```bash
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
cd dashboard && npm install && cd ..
php artisan serve        # backend: http://localhost:8000
cd dashboard && npm run dev   # dashboard: http://localhost:3000
```

Source: https://github.com/JOHNBSE/live-chat

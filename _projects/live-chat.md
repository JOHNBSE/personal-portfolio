---
title: Live Chat — v1.0
repo_url: https://github.com/JOHNBSE/live-chat
image: /assets/images/live-chat-placeholder.svg
excerpt: "A multi-tenant live chat platform (Laravel 12, React dashboard)."
---

A multi-tenant live chat platform. Admins register, create sites, and embed a lightweight JavaScript widget on any website. Visitors chat through the widget; admins respond via the React dashboard.

## Tech Stack

- Laravel 12 (PHP 8.2+)
- Laravel Sanctum, Vite, Tailwind CSS
- React dashboard (separate frontend)

## Project Structure

See the repository for full structure. Key files include `routes/api.php`, `public/widget.js`, and the React dashboard under `dashboard/`.

## How it works

An admin creates a Site which generates a `site_key`. The widget uses the key to open conversations and poll the server for updates (v1 uses HTTP polling; v2 will use WebSockets).

Source: https://github.com/JOHNBSE/live-chat

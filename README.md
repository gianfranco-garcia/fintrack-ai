# FinTrack AI — AI-Powered Personal Finance Tracker

> Log your expenses by chatting in natural language; an LLM parses them and a live dashboard visualizes your spending, savings, and debt — in real time.

## Problem
Tracking personal finances is tedious — manual spreadsheets and clunky apps. I wanted something effortless: just text what I spent, in plain language, and see it all in a clean dashboard.

## Solution
An **end-to-end system**: I message a Telegram bot in natural language (e.g. *"200 shoes wells"*), an AI (Claude Sonnet 4.6) interprets it into structured data, stores it in Google Sheets, and a custom web app visualizes everything live — accessible as an app on my phone.

## Architecture
**Telegram → n8n + Claude Sonnet 4.6 → Google Sheets → Web App (Netlify)**
(See `architecture-diagram.html` for the visual.)

## Tech stack
- **n8n** — workflow automation (the ingestion pipeline)
- **Claude Sonnet 4.6** — LLM that interprets natural-language messages into JSON
- **Google Sheets** — database + financial calculations (formulas)
- **JavaScript / HTML / CSS** — custom web app (no framework)
- **Netlify** — free hosting (live, installable PWA)

## Key features
- 🗣️ **Natural-language logging** (English + Spanish) via Telegram chat
- 🤖 **AI categorization** into 9 categories with reliable structured output
- 📊 **Live dashboard:** spending breakdown (donut + bars), monthly + cumulative savings, Discover credit-card debt tracking with available credit, and **intelligent gambling P&L** (only counts as spending on a net loss)
- 🌗 **Dark/light theme**, mobile-installable (add to home screen)
- 🗓️ **Month-by-month navigation**

## What I built / learned
- Designed a full **data pipeline**: input → AI parsing → storage → visualization
- **Prompt engineering** for reliable, structured JSON output (and handling edge cases, e.g. quantity vs. price)
- **Data modeling & business logic** (savings, debt, net gambling), separating the **raw ledger** (Google Sheets stores facts) from the **presentation layer** (the app interprets them) — a clean, professional architecture
- Fetching & parsing **Google Sheets data** in a web app (incl. the date-parsing gotcha)
- **Deploying** a static web app and making it a phone-installable PWA

## Links
- 🔗 **Live dashboard (sample data):** https://effulgent-marigold-d342e1.netlify.app
- 💻 **Source code:** this repository (`webapp.html`)
- 🎥 **Demo video:** _coming soon_

---
*Built by Gianfranco García — Business Analytics @ FIU*

# FinTrack AI — AI-Powered Personal Finance Tracker

> Log your expenses by chatting in natural language; an LLM parses them and a live dashboard visualizes your spending, savings, and debt — in real time.

## Executive Summary
FinTrack AI is an end-to-end personal finance system that turns a plain-language text message into a live, visual dashboard. Instead of manual spreadsheets, I text what I spent — e.g. *"100 restaurant wells"* — and an AI logs, categorizes, and visualizes it automatically, tracking spending, savings, and credit-card debt in real time. I built the whole system solo: the data pipeline, the AI integration, the financial logic, and the deployed, phone-ready app.

## Problem
Tracking personal finances is tedious — manual spreadsheets and clunky apps. I wanted something effortless: just text what I spent, in plain language, and see it all in a clean dashboard.

## Solution
An **end-to-end system**: I message a Telegram bot in natural language (e.g. *"100 restaurant wells"*), an AI (Claude Sonnet 4.6) interprets it into structured data, stores it in Google Sheets, and a custom web app visualizes everything live — accessible as an app on my phone.

## Architecture
**Telegram → n8n + Claude Sonnet 4.6 → Google Sheets → Web App (Netlify)**
(See `architecture-diagram.html` for the visual.)

The complete automation is in **[`n8n-workflow.json`](n8n-workflow.json)** — the exportable n8n workflow (importable into any n8n instance), including the AI agent's full categorization prompt. Sanitized for sharing: the real Google Sheet ID is replaced with a placeholder and no credentials are included.

## Tech stack
- **n8n** — workflow automation (the ingestion pipeline)
- **Claude Sonnet 4.6** — LLM that interprets natural-language messages into JSON
- **Google Sheets** — database + financial calculations (formulas)
- **JavaScript / HTML / CSS** — custom web app (no framework)
- **Netlify** — free hosting (live, installable PWA)

## Key features
- 🗣️ **Natural-language logging** (English + Spanish) via Telegram chat
- 🤖 **AI categorization** into 9 spending categories, straight from the chat message
- 📊 **Live dashboard:** spending breakdown (donut + bars), monthly + cumulative savings, Discover credit-card debt tracking with available credit, and a **conditional net-P&L rule** (an activity only counts as spending on a net loss)
- 🌗 **Dark/light theme**, mobile-installable (add to home screen)
- 🗓️ **Month-by-month navigation**

## What I built / learned
- Designed a full **data pipeline**: input → AI parsing → storage → visualization
- **Prompt engineering** for reliable, structured JSON output (and handling edge cases, e.g. quantity vs. price)
- **Data modeling & business logic** (savings, debt, conditional net-P&L), separating the **raw ledger** (Google Sheets stores facts) from the **presentation layer** (the app interprets them), so the stored data stays trustworthy even when I change how the dashboard looks
- Fetching & parsing **Google Sheets data** in a web app (incl. the date-parsing gotcha)
- **Deploying** a static web app and making it a phone-installable PWA

## Impact & Results
- ⏱️ **Tackles the biggest reason budgeting fails — friction.** Logging an expense takes a ~5-second text instead of minutes of manual spreadsheet entry.
- 🔄 **A real, daily-used system, not a demo** — reliable enough that I track my own finances with it every day.
- 🧠 **Reliable AI output:** every message is parsed into structured, validated data and auto-sorted into 9 spending categories (handling tricky edge cases like quantity vs. price).
- 🏗️ **Demonstrates the full data lifecycle** — ingestion → AI parsing → data modeling → storage → visualization → deployment — the same end-to-end flow a Data/Business Analyst works across.

## Links
- 🎥 **Demo video (57s):** https://www.youtube.com/watch?v=D5Ww1O485H0
- 🔗 **Live dashboard (sample data):** https://effulgent-marigold-d342e1.netlify.app
- 💻 **Source code:** this repository (`webapp.html` for the app, `n8n-workflow.json` for the automation pipeline)

---
*Built by Gianfranco García — Business Analytics @ FIU*

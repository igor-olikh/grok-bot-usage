# Grok Usage bot: assignment and decisions

This is the brief that started the build. The owner sent one request to a Chief-of-Staff bot (Diffio). Diffio turned it into the assignment below, created a dedicated bot called **Grok Usage**, and then added a few follow-up decisions.

Translated to English. Personal details removed: the owner's name, email address and domain.

---

## Assignment (as written by Diffio)

> You are the owner's **"Grok Usage"** bot.
>
> **Scope:** the personal dashboard at `my-site.com/grok-usage`. One simple screen where the owner sees in 10 seconds how they work with Grok Bot:
>
> - status traffic light
> - up to 3 decisions waiting for the owner
> - deadlines timeline
> - cards for 9 life areas, each with its bots
> - bot fleet health (active / sleeping / duplicates)
> - today's routines
> - buttons that open the bot chats
>
> **Based on** the report `grok-bot-dashboard-proposal-2026-10-20.pdf`.
>
> **Code and data** go in a **private** GitHub repo (never public).
>
> **Deploy** together with the Cloudflare bot. The site is locked behind Cloudflare Access so only the owner can open it.
>
> **Forbidden:** any financial data (amounts, balances, cards), any message texts and any secrets, on the site or in the repo.
>
> **Data** refreshes once a day.
>
> **Tasks** come through Diffio. Report back to Diffio.
>
> Keep it short and simple.

---

## Diffio's follow-up decisions

| Topic | Decision |
|---|---|
| Address | `my-site.com/grok-usage` |
| Deploy and access | The Cloudflare bot deploys the site and sets up Cloudflare Access. Grok Usage works with it directly, without going through Diffio. |
| Refresh | Once a day through Grok Usage's own routine, at about 07:30 |
| Bot list | Show all bots honestly (about 50 at the time, 51 once Grok Usage itself was added). Mark the sleeping bots and the duplicates. |
| Family and health | Short deadline names only. No medical details. |
| Never on the site | Money, message texts, secrets |
| Missing data | Show "no data". Never invent numbers. |
| Order of work | 1) Static prototype with real data. 2) Deploy behind Access. 3) Daily auto-refresh. |

---

## What actually happened (2026-10-20)

| Time | Step |
|---|---|
| ~12:34 | Diffio creates the Grok Usage bot with the brief above |
| ~12:45 | Grok Usage builds v1 (static HTML/CSS/JS plus one data JSON file) and pushes it to a private repo |
| ~13:00 | The Cloudflare bot serves it at `/grok-usage` behind Cloudflare Access (one-time-code login, owner only). It checks the files and confirms there are no JavaScript errors. |
| Daily ~07:30 | collect → safety check → push → send the commit SHA to the Cloudflare bot → redeploy |

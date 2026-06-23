# UThuya Stock Manager

Bulk image upload dashboard for UThuya online clothing shop.

## Features

- 📤 Drag-and-drop multi-image upload (up to 10 at once)
- 🤖 AI auto-detection (category + color via Gemini Vision)
- ✏️ Per-card inline editing with manual save
- ✅ Batch publish to live products table
- 📱 Mobile-first design (Tailwind + Alpine.js)

## Stack

- Single-file HTML SPA (Vanilla JS + Tailwind CDN + Alpine.js)
- Backend: n8n workflows + Supabase + VPS disk storage
- No build step — drop-in deployment

## Live

→ https://moehtetofficial.github.io/uthuya-stock-manager/

## Config

First-time setup: open Settings (gear icon) and configure:

- **Upload Endpoint** — `https://n8n.srv1695682.hstgr.cloud/webhook/uthuya-bulk-upload`
- **Drafts API** — `https://n8n.srv1695682.hstgr.cloud/webhook/uthuya-drafts-api`
- **Upload Token** — shared secret with n8n
- **Admin Token** — shared secret with n8n

Settings persist in browser localStorage.

## Workflow

1. Drop images → backend saves to VPS + AI detects category/color
2. Cards appear pre-filled — review and edit price, size, stock, etc.
3. Save each card individually
4. Click "Publish All" → all saved drafts go live in `products` table
5. `uthuya_kb_embedding` cron picks up new rows for vector indexing

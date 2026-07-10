# Patty's Smash Burger — Order Management

Three static web pages for a smash burger joint: **customer order tracking**, **menu browsing**, and a **live TV order board**. Built with vanilla HTML/CSS/JS, powered by Supabase, hosted on Vercel.

## Pages

| Page | File | Purpose |
|---|---|---|
| **Order Tracking** | `index.html` | Customers enter their order number to see live status with a two-step timeline, countdown timer, and audio alerts. Supports `?order_id=N` deep linking. |
| **Menu** | `menu.html` | Grid of menu categories (Burgers, Sandwiches, Wraps, Sides, Drinks) with tap-to-zoom lightbox. |
| **TV Board** | `tv.html` | 1080p real-time order board for in-store screens. Two columns ("Preparing" / "Ready for Pickup") polling Supabase every second. Auto-fullscreen on first click. |

## Features

- **Live polling** from Supabase REST API (5s for tracking, 1s for TV)
- **Two-stage status:** Preparing Food → Ready for Pickup
- **Elapsed time counter** — freezes and shows total when order is ready
- **Audio notifications** — `ready.mp3` on order-ready, Web Audio API oscillator on cancel
- **Order search history** — last 5 orders stored in `localStorage`
- **Archived order fallback** — checks `completed_orders` table
- **Canceled/sent-back detection** with toast + descending tone
- **Trilingual:** English, Français, العربية (full RTL support)
- **Menu lightbox** — full-screen pinch-to-zoom
- **TV smart sorting** — preparing by order number asc, ready by recency
- **Language rotation on TV** — cycles every 5s
- **QR code** on TV for customers to scan
- **Responsive** — breakpoints at 480px, 600px, 768px
- **Vibration API** feedback on mobile

## Stack

| Layer | |
|---|---|
| Frontend | Vanilla HTML5, CSS3, JS |
| Backend | Supabase (PostgreSQL REST API) |
| Hosting | Vercel |
| Fonts | FoodBuka (headings), Cairo (body) |
| Audio | Web Audio API + HTMLAudioElement |

## Supabase Tables

- **`live_orders`** — active orders (`order_number`, `status`, `created_at`, `updated_at`, ...)
- **`completed_orders`** — archived orders

## Assets

- `assets/fonts/` — FoodBuka.woff2, Cairo.ttf (regular/bold), AuthorMedium.ttf, Fuchas.ttf
- `assets/images/` — logo.png, qr-code.svg, menu photos (5 `.jpeg`/`.jpg`)
- `assets/sounds/` — ready.mp3

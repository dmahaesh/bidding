# GAVEL — Live-Auction PWA (demo)

A mobile-first progressive web app for real-time bidding, plus a seller console.
Fully client-side: state lives in the browser (`localStorage`), no backend required.
Bot bidders drive live activity, funds are held/refunded on outbid, and an
anti-snipe clock resets to 1:00 on any last-minute bid.

## Demo logins

| App | URL | Email | Password |
|-----|-----|-------|----------|
| Buyer / store | `/` | `demo@gavel.app` | `demo123` |
| Seller console | `/admin` | `admin@gavel.app` | `admin123` |

> On each login screen there's a **"tap to fill"** box — click it to auto-fill the
> credentials, then hit **Sign in**. Login is remembered per browser; use **Sign out**
> (buyer: Wallet tab · seller: top-right) to return to the login screen.

## Try it

1. Sign in to the **store** and bid on a lot — quick-bid buttons, a custom amount,
   or arm **auto-bid** and let it counter rivals up to your max.
2. Open the **seller console** (`/admin`), publish a new lot — it appears live in
   the store within ~1.5s, with bots bidding against you.
3. Watch the **anti-snipe** clock reset when a bid lands inside the final minute.

## Pages / files

- `index.html` — entry point, redirects to the buyer store.
- `Gavel Auctions.dc.html` — the buyer app (feed, browse, ended, my bids, wallet).
- `Gavel Admin.dc.html` — the seller console (`/admin`).
- `support.js`, `image-slot.js` — generated runtime (do not edit by hand).
- `images/` — product photos used by the seeded lots.

## Run locally

Any static file server works, e.g.:

```bash
npx serve .
# then open http://localhost:3000
```

Opening the files directly via `file://` also works, but a server is closer to production.

## Deploy (Vercel)

This is a static site — no build step.

- **Via GitHub:** import the repo in Vercel, framework preset **"Other"**,
  build command empty, output directory **`.` (root)**. Every push auto-deploys.
- **Via CLI:** `npm i -g vercel && vercel` (accept the defaults) then `vercel --prod`.

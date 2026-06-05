# Mason Jar Films — Infrastructure Reference Sheet
## One-Page Quick Reference

---

## Hosting Stack

```
masonjarfilms.com
      ↓
Squarespace (domain registrar only — renews Apr 2027)
      ↓ nameservers: mina.ns.cloudflare.com / tate.ns.cloudflare.com
Cloudflare (jones@masonjarfilms.com)
      ↓ Workers routing
Cloudflare Workers — "masonjarfilms" project
      ↓ pulls from
GitHub — masonjarfilms/masonjarfilms-site (main branch)
```

---

## Cloudflare Account

**Login:** jones@masonjarfilms.com
**Dashboard:** dash.cloudflare.com

| What | Where in Dashboard |
|---|---|
| DNS records | Domains → masonjarfilms.com → DNS → Records |
| Nameservers | Domains → masonjarfilms.com → scroll down |
| Workers/site | Workers & Pages → masonjarfilms |
| Custom domains | Workers & Pages → masonjarfilms → Domains |
| Deploy status | Workers & Pages → masonjarfilms → Deployments |
| SSL certificates | Domains → masonjarfilms.com → SSL/TLS → Edge Certificates |

**Critical DNS records (do not delete):**
- 5× MX records → Google (email routing)
- TXT `google-site-verification` → Google Workspace verification
- TXT `v=DKIM1` → email authentication
- Worker record → masonjarfilms.com → masonjarfilms Worker
- Worker record → www.masonjarfilms.com → masonjarfilms Worker

**Nameservers (must always be):**
- `mina.ns.cloudflare.com`
- `tate.ns.cloudflare.com`

⚠️ WARNING: A second Cloudflare account exists at `welcome@masonjarfilms.com` (set up by VA for Mailgun). Ignore any emails from that account. Never change nameservers based on emails from Cloudflare — verify in the `jones@` dashboard first.

---

## GitHub

**Account:** masonjarfilms (jones@masonjarfilms.com)
**Repo:** github.com/masonjarfilms/masonjarfilms-site
**Branch:** main
**Local folder:** /Users/jones/Business/Mason Jar/Website 2026/masonjarfilms

Every push to main → Cloudflare auto-deploys within ~60 seconds.

---

## Formspree (Contact Form)

**Login:** jones@masonjarfilms.com at formspree.io
**Form endpoint:** https://formspree.io/f/mojbwzgl
**Submissions go to:** jones@masonjarfilms.com
**Spam protection:** `_gotcha` honeypot field built into form

---

## File Structure

```
masonjarfilms/
├── index.html          ← Home (video fade, hero content)
├── films.html          ← Films (Mediazilla embeds go here)
├── about.html          ← About (drop photos in assets/images/)
├── contact.html        ← Contact (Formspree form)
├── netlify.toml        ← Legacy — can be ignored
├── css/
│   └── main.css        ← All styles
├── fonts/
│   └── Delicious-*.woff2  ← Brand fonts (loaded via fonts/stylesheet.css)
└── assets/
    ├── logos/
    │   ├── mjf-logo-horizontal.svg
    │   └── mjf-monogram.svg
    ├── images/
    │   ├── chris-1976.jpg        ← TODO: drop in
    │   └── chris-austin-bw.jpg   ← TODO: drop in
    └── video/
        └── homepage-loop.mp4     ← Test clip in place; final TBD
```

---

## Design Tokens

```css
--bg: #ede8de;                    /* Warm paper */
--dark: #1a120a;                  /* Film dark */
--ink: #1c120a;                   /* Primary text */
--ink-muted: rgba(28,18,10,0.55); /* Secondary text */
--accent: #7a5030;                /* CTAs, italic highlights */
```

**Fonts:** Delicious (self-hosted WOFF2) → fallback: Libre Baskerville (Google Fonts) → Georgia
**UI font:** Inter (Google Fonts)

---

## Squarespace (Domain Only)

**Login:** jones@masonjarfilms.com at squarespace.com
**Purpose:** Domain registration only. Website subscription cancelled June 2026.
**Domain renews:** April 13, 2027 — $20/yr — AUTO-RENEW IS ON
**Nameservers set to:** mina + tate (Cloudflare)
**Do not:** change nameservers, add DNS presets, or reconnect to a Squarespace website

---

*Mason Jar Films — June 2026*

# Mason Jar Films — Website SOP
## Standard Operating Procedure: Making Changes & Deploying

---

## Overview

The website is a static HTML/CSS site. Making a change involves three steps:
1. Edit the file on your computer
2. Commit the change in GitHub Desktop
3. Push to GitHub → Cloudflare auto-deploys

No build process. No command line required for most tasks.

---

## SOP 1 — Making a Code Change

**Tools needed:** GitHub Desktop, a text editor (VS Code recommended)

1. Open your `masonjarfilms` folder in VS Code
2. Edit the relevant file(s)
3. Save
4. Open **GitHub Desktop**
5. You'll see changed files listed on the left
6. Type a brief summary in the **Summary** box (e.g., "update films page embed")
7. Click **Commit to main**
8. Click **Push origin**
9. Wait ~60 seconds
10. Refresh masonjarfilms.com to confirm changes are live

**To check deployment status:** Cloudflare dashboard → Workers & Pages → masonjarfilms → Deployments

---

## SOP 2 — Adding a Homepage Video

**File requirements:**
- Name: `homepage-loop.mp4` (exact — case sensitive)
- Format: H.264 MP4
- Resolution: 1080p (1920×1080)
- Size: Under 25MB (Cloudflare hard limit) — target under 10MB
- Length: Currently timed for ~9 seconds (fade triggers at 9000ms in index.html)

**To change fade timing:** Open `index.html`, find `}, 9000);` and change the number (milliseconds).

**Steps:**
1. Export/compress video in HandBrake: General → Fast 1080p30, RF slider at 24
2. Name it `homepage-loop.mp4`
3. Drop into `masonjarfilms/assets/video/` — replace existing file
4. Commit and push via GitHub Desktop

**To test locally without deploying:**
```
cd ~/Business/Mason\ Jar/Website\ 2026/masonjarfilms
python3 -m http.server 8000
```
Open `http://localhost:8000` in Chrome. Hard refresh with Cmd+Shift+R after swapping video.

---

## SOP 3 — Adding Mediazilla Embeds (Films Page)

1. In Mediazilla, get the embed code for your film
2. Open `films.html` in VS Code
3. Find the comment that says `<!-- EMBED GOES HERE -->`
4. Paste your Mediazilla iframe code there
5. On the parent div (`.featured-film` or `.grid-film`), add class `has-embed` to hide the placeholder play button
6. Commit and push

**There are two embed slots:**
- Hero film (top of page) — inside `.featured-film`
- Natalie & Jack (grid) — inside `.grid-film`

---

## SOP 4 — Adding About Page Photos

1. Prepare two images:
   - `chris-1976.jpg` — color still, square crop works best
   - `chris-austin-bw.jpg` — B&W mirror shot, square crop works best
2. Drop both into `masonjarfilms/assets/images/`
3. Open `about.html` in VS Code
4. Find the two commented-out `<img>` tags (search for `Uncomment`)
5. Uncomment each `<img>` tag by removing the `<!--` and `-->` wrapper
6. The placeholder gradient divs above each img tag can be deleted or left in place (the image will cover them)
7. Commit and push

---

## SOP 5 — Updating Contact Form Email

If you need form submissions to go to a different email:
1. Log into formspree.io with jones@masonjarfilms.com
2. Go to your form (mojbwzgl)
3. Settings → Email notifications → update address

No code changes needed.

---

## SOP 6 — DNS Troubleshooting

**If the site stops loading:**

First, verify nameservers are correct:
1. Log into Squarespace → Domains → masonjarfilms.com → Domain Nameservers
2. Should show: `mina.ns.cloudflare.com` and `tate.ns.cloudflare.com`
3. If they show anything else — change them back immediately

Second, verify Cloudflare Workers are active:
1. Log into Cloudflare (jones@masonjarfilms.com)
2. Workers & Pages → masonjarfilms → Deployments
3. Should show a recent successful deployment

Third, check DNS propagation:
1. Go to dnschecker.org
2. Search `masonjarfilms.com` with record type A
3. Results should NOT show 198.185.159.x or 198.49.23.x (those are Squarespace IPs)

**⚠️ Critical warning:** There is a second Cloudflare account at `welcome@masonjarfilms.com` used for email/Mailgun. Ignore any automated emails from that account about nameservers. Always verify in the `jones@` account dashboard before changing anything in Squarespace.

---

## SOP 7 — Local Development Server

Use this to preview changes without deploying (saves Cloudflare bandwidth):

1. Open **Terminal** (Applications → Utilities → Terminal)
2. Paste:
```
cd ~/Business/Mason\ Jar/Website\ 2026/masonjarfilms && python3 -m http.server 8000
```
3. Open Chrome → `http://localhost:8000`
4. Leave Terminal open while testing
5. Hard refresh with **Cmd+Shift+R** after any file change
6. Close Terminal when done

---

## Batch Your Deployments

Each push to GitHub = one Cloudflare deploy. Group multiple changes into one commit when possible. Test locally first, then push everything at once.

---

## SOP 8 — Starting a New Claude Conversation for Website Work

Always upload files from your **local desktop folder** — not from Claude artifacts or GitHub. Your local folder is the source of truth.

**Folder location:** `/Users/jones/Business/Mason Jar/Website 2026/masonjarfilms/`

**Upload these files at the start of every session:**

| File | Why |
|---|---|
| `MJF_Website_Transition_Brief.md` | Full project history and context |
| `MJF_Infrastructure_Reference.md` | Accounts, DNS, stack overview |
| `index.html` | Home page code |
| `films.html` | Films page code |
| `about.html` | About page code |
| `contact.html` | Contact page code |
| `css/main.css` | All styles |

That's your complete context package. Any Claude session with those files can make changes, debug issues, or build new features immediately.

**Note on campaign landing pages:** These were not built in the "Website — Build" conversation. Find them in whichever conversation created them, or build fresh. They are separate from the four core pages above.

**After making changes in Claude:** Always download the updated files and replace them in your local desktop folder before committing via GitHub Desktop. Never push artifacts directly from Claude — always route through your local folder.

---

## Files You Should Never Delete

| File | Why |
|---|---|
| `fonts/stylesheet.css` | Required for Delicious font loading |
| `fonts/Delicious-*.woff2` | Brand fonts — if deleted, fallback to Baskerville |
| `assets/logos/mjf-logo-horizontal.svg` | Nav logo all pages |
| `assets/logos/mjf-monogram.svg` | Footer seal all pages |
| `css/main.css` | All site styles |

---

*Mason Jar Films — June 2026*

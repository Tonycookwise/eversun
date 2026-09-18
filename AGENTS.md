# AGENTS.md — Eversun Brand Website (Handoff Guide)

> This file is the handoff briefing for any AI coding agent (Codex, etc.) taking over this project. Read it fully before making changes.

## Project Overview

A static B2B brand showcase website for **Yangjiang Eversun Houseware Co., Ltd.** (kitchenware manufacturer/exporter, Yangjiang, Guangdong, China). Pure HTML/CSS/JS — no build step, no framework, no dependencies.

- **Live site**: https://www.yjeversun.com
- **GitHub repo**: https://github.com/Tonycookwise/eversun (branch `main`)
- **Hosting**: GitHub Pages, `Deploy from a branch` → `main` / root. Custom domain `www.yjeversun.com` configured with Enforce HTTPS.
- **DNS**: `www` CNAME → `tonycookwise.github.io`; apex A records → GitHub Pages IPs (185.199.108-111.153)

## File Structure

| Path | Purpose |
|------|---------|
| `index.html` | Single-page brand site (~60KB). All CSS/JS inline. Sections: Hero, About (with mouse-hover 3-image slider), Products (8 categories, modal popups), Certifications, OEM/ODM, Canton Fair photo gallery (horizontal scroll, 4 photos), Contact. |
| `Eversun_Catalog_2026.html` | Full product e-catalog (~620KB). SPA-style: sidebar navigation + JS page mapping. Uses `images/p003_00.jpg`-style assets (~2600 files, compressed from original PPT export). |
| `images/` | All site + catalog images (~42MB, ~2600 files). Site photos: `logo.png`, `office.jpg`, `showroom.jpg`, `office-2.jpg`, 8 category JPGs, `canton-fair-1.jpg` ~ `canton-fair-4.jpg`, `favicon.png` is at repo root. Catalog images follow `pXXX_XX.jpg` naming from original PPT page/slide indices. |
| `CNAME` | GitHub Pages custom domain file (`www.yjeversun.com`). Do not delete or edit. |
| `favicon.png` | 32×32, generated from `images/logo.png`. |

## Design System

- **Brand colors**: forest green `#1B4332` (primary), gold `#C9972C` (accent), cream `#FBFAF5` (light background). Check `:root` CSS variables in `index.html`.
- **Fonts**: Playfair Display (display numbers/titles) + system sans-serif.
- **Style**: card-based layout, `border-radius`, gold hover borders, scroll-reveal animations via Intersection Observer (`.reveal` class).

## Content Facts (do not change without owner approval)

- Email: `tony@yjeversun.com` · WhatsApp/WeChat: `+86-015219359767`
- Certifications displayed: FDA, LFGB, BSCI, ISO 9001, BRCGS (no CE/RoHS)
- 8 product categories: Kitchen Gadgets, Kitchen Utensils, Tea Infuser, Food Tongs, Bakeware, Silicone Tools, BBQ Tools, Knife and Scissors
- Hero subtitle is deliberately 3 lines (max-width 740px)
- Canton Fair gallery has exactly 4 photos (5/6 were removed due to orientation issues)

## Workflow for Changes

```bash
git add <files>
git commit -m "clear message"
git push            # SSH auth via ~/.ssh/id_ed25519, already configured on owner's Mac
```

GitHub Pages redeploys automatically in 1–2 minutes. Verify with `curl -sI https://www.yjeversun.com/...`. Note: CDN may cache up to 10 min (`cache-control: max-age=600`); use a `?cb=$(date +%s)` query param to bust cache when verifying images.

## Known Quirks / Warnings

1. **Loose root-level JPGs** (`BBQ Tools.jpg`, `Bakeware.jpg`, `Kithen Gadgets.jpg` — note the typo — etc.) are **untracked duplicates** of files already in `images/`. Do NOT add them to git; the site does not reference them. (Note: `Kithen Gadgets.jpg` filename typo is intentional to match original source, ignore it.)
2. `images/` contains ~2600 catalog images. When adding/renaming catalog images, grep `Eversun_Catalog_2026.html` for `src="images/` references first and copy only what's referenced.
3. Catalog images are the **compressed versions** (1200px). Original uncompressed versions (~1.2GB) must never be pushed — repo bloat / GitHub size limits.
4. `.workbuddy/` and `.DS_Store` are gitignored.
5. Git user identity on this machine: `Tonycookwise <tony@yjeversun.com>`.

## Typical Tasks You May Be Asked To Do

- Swap a photo: replace the JPG in `images/` (same filename, ≤1200px, <400KB), push.
- Edit text/sections: edit `index.html` (sections are commented), push.
- Update catalog entries: edit `Eversun_Catalog_2026.html` — product titles appear in sidebar nav buttons, section titles, and a JS page-mapping object; update all occurrences consistently.
- Keep single-file architecture (inline CSS/JS) unless owner requests otherwise.

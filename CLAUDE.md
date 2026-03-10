# Portfolio — Project Guide

**Local path:** `C:\Users\adamb\OneDrive\Desktop\Portfolio\portfolio`
**GitHub repo:** https://github.com/adam-cott/portfolio
**Live site:** Deployed via GitHub Pages (auto-deploys on push to `main`)

---

## Tech Stack

| Layer | Choice |
|---|---|
| Framework | [Quarto](https://quarto.org/) — markdown-based static site |
| Theme | Cosmo (Bootstrap-based) |
| Custom styles | `styles.css` |
| Icons | Font Awesome 6.4.0 (CDN) |
| Deploy | GitHub Pages via `.github/workflows/` CI/CD |

Build output goes to `_site/`. Never manually edit files inside `_site/` — it is auto-generated.

---

## File Structure

```
portfolio/
├── index.qmd           # Homepage — hero banner, bio, skills, featured projects
├── about.qmd           # About page — extended personal bio
├── problems.qmd        # "Problems I'm Exploring" page (currently hidden from nav)
├── _quarto.yml         # Site config — nav, theme, format settings
├── styles.css          # All custom CSS (teal theme, hero banner, problem cards, etc.)
├── images/
│   ├── profile.jpg     # Profile photo used in hero banner on home + about pages
│   └── favicon.png     # Browser tab icon
├── projects/
│   ├── project-1.qmd  # SpendTrackr (LIVE — shown in nav)
│   ├── project-2.qmd  # (exists but commented out in nav)
│   ├── project-3.qmd  # (exists but commented out in nav)
│   ├── project-4.qmd  # (exists but commented out in nav)
│   ├── project-5.qmd  # (exists but commented out in nav)
│   └── project-6.qmd  # (exists but commented out in nav)
├── _site/              # Auto-generated build output — do not edit manually
├── .github/workflows/  # CI/CD for GitHub Pages auto-deploy
└── CLAUDE.md           # This file
```

---

## Navigation (\_quarto.yml)

Current navbar state:
- **Home** (`index.qmd`) — visible
- **About** (`about.qmd`) — visible
- **Problems I'm Exploring** (`problems.qmd`) — **HIDDEN** (commented out)
- **Projects** dropdown — visible
  - SpendTrackr (`projects/project-1.qmd`) — visible
  - project-2 through project-6 — commented out

### To restore "Problems I'm Exploring":
Uncomment these two lines in `_quarto.yml` under `website.navbar.left`:
```yaml
#- href: problems.qmd
#  text: Problems I'm Exploring
```

### To add a project to the nav:
Uncomment the relevant line(s) under the Projects dropdown menu in `_quarto.yml`.

---

## Design System (styles.css)

**Color palette — Professional Teal Theme:**

| Variable | Hex | Use |
|---|---|---|
| `--primary-teal` | `#0A7C7A` | Buttons, links, accents |
| `--accent-teal` | `#4A9D9C` | Hover states |
| `--dark-teal` | `#064E4D` | Headings, navbar background |
| `--light-teal` | `#E0F2F1` | Backgrounds, borders, card fills |
| `--charcoal` | `#2C3E50` | Body text |
| `--medium-gray` | `#6B7280` | Secondary text |

**Key CSS classes:**
- `.hero-banner` — centered card with teal gradient background; used on home + about pages
- `.problem-card` — white card with left teal border; used on problems page
- `.g-col-12.g-col-md-6.card` — project card on homepage

---

## Pages

### index.qmd — Homepage
- Hero banner with `images/profile.jpg` (280px circle), name, LinkedIn + GitHub buttons
- Sections: "Turning Strategy Into Execution", Background, What You'll Find Here, Skills, Featured Projects
- Featured Projects card links to SpendTrackr (`projects/project-1.qmd`)
- LinkedIn: https://www.linkedin.com/in/adam-cottrell-759344265/
- GitHub: https://github.com/adam-cott

### about.qmd — About
- Same hero banner layout as homepage
- Extended bio: BYU Strategic Management, TA for STRAT 392, LA missionary (2 years, fluent Spanish), tech interest
- Personal: hiking, guitar, singing, U.S. national parks goal

### problems.qmd — Problems I'm Exploring
- Currently hidden from nav (see above to restore)
- 5 problem cards: Explaining Meaningful Work Simply, Deciding What Matters Most, Making Frameworks Feel Real, Small Things That Slow You Down, Knowing When Good Enough Is Good Enough

### projects/project-1.qmd — SpendTrackr
- Stack: JavaScript, HTML/CSS, Supabase (PostgreSQL + auth + storage), Vercel, PWA, OCR, Gmail API
- Live app: https://spendtrackr-five.vercel.app/
- GitHub: https://github.com/adam-cott/spendtrackr
- Features: OCR receipt scanning, 529 vs non-529 expense tracking, PIN security, Gmail notifications, cloud sync

---

## Common Commands

```bash
# Preview site locally (requires Quarto CLI installed)
quarto preview

# Build site
quarto render

# Publish (Quarto's built-in GitHub Pages deploy)
quarto publish gh-pages
```

Auto-deploy also triggers on every push to `main` via `.github/workflows/`.

---

## Important Notes for AI Assistants

- **`_site/` is auto-generated** — never edit files there directly; edit `.qmd` source files instead
- **Nav items are toggled by commenting/uncommenting** in `_quarto.yml` — the `.qmd` files always exist; visibility is controlled in the config
- **"Problems I'm Exploring" is intentionally hidden** — `problems.qmd` exists and is intact; just commented out of the nav
- **Projects 2–6 are placeholder files** — they exist in `projects/` but are commented out of the nav until content is ready
- **Font Awesome is loaded via CDN** in `_quarto.yml` under `include-in-header` — required for LinkedIn/GitHub icons and project page icons
- **Theme is Cosmo** — Bootstrap-based; `styles.css` overrides it with the teal palette; avoid fighting Bootstrap specificity without `!important` where needed

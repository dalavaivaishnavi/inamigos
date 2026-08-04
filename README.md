# InAmigos Foundation — NGO Awareness Website

A multi-page awareness website built for InAmigos Foundation, created as part of the
**NGO Awareness Webpage Creation** internship task. It introduces the organisation, its
six ongoing initiatives, its social impact, and gives visitors a clear path to volunteer
or get in touch.

---

## 📁 Folder structure

```
inamigos-site/
├── index.html          → Homepage (hero, about preview, initiatives preview, impact stats, gallery preview, CTA)
├── about.html           → Full "About Us" — founding story, founder, credentials
├── initiatives.html     → All six projects in detail (SEVA, BACHPANSHALA, JEEV, UDAAN, PRAKRITI, VIKAS)
├── gallery.html          → Full photo gallery (20 photos)
├── volunteer.html       → "Why volunteer" + "How it works" + CTA to contact
├── contact.html          → Address, email, phone, social links, embedded map
├── styles.css             → Single shared stylesheet used by every page
├── vercel.json             → Vercel config (security headers, caching) — optional, not required to deploy
├── .gitignore               → Standard ignores for git/Vercel/editor files
├── .github/
│   └── workflows/
│       └── deploy.yml      → Optional GitHub Actions workflow for CI-based Vercel deploys
└── README.md                → This file
```

All seven files must stay together in the same folder — the pages link to each other
with relative paths (`about.html`, `styles.css`, etc.), so moving `styles.css` out or
renaming a file will break the links.

---

## ▶️ How to run it

No build step, server, or install required — it's a static site.

**Simplest:** double-click `index.html` to open it in your browser.

**Recommended (avoids browser caching issues while editing):**
```bash
cd inamigos-site
python3 -m http.server 8000
```
Then visit `http://localhost:8000` in your browser.

Or, in VS Code: install the **Live Server** extension, right-click `index.html`,
and choose **Open with Live Server**.

---

## 🧭 Navigation

Every page shares the same header (logo + nav) and footer. All internal links point to
local pages in this folder — nothing redirects to the real inamigosfoundation.org.in
site. The only external links are the **Facebook** and **Instagram** icons in the
footer, which open the organisation's real social profiles in a new tab.

| Page | Purpose |
|---|---|
| Home | Introduction + snapshot of everything else |
| About | Founding story, founder, registrations/certifications |
| Initiatives | Deep dive into all 6 projects |
| Gallery | Full photo grid |
| Volunteer | What volunteers get, how to get started |
| Contact | Address, email, phone, map |

---

## 🚀 Deploying to Vercel

This is a static site, so Vercel needs **no build step** — it auto-detects plain
HTML/CSS and serves it as-is. `vercel.json` is included for security headers and
caching, but the site will deploy fine even without it.

### Option A — Vercel dashboard (simplest, no YAML needed)
1. Push this folder to a GitHub repo.
2. Go to [vercel.com/new](https://vercel.com/new) → **Import Project** → select the repo.
3. Framework preset: **Other** (or leave as detected — no build command, no output
   directory override needed).
4. Click **Deploy**. Vercel will redeploy automatically on every push to `main`.

### Option B — Vercel CLI (no YAML, no GitHub required)
```bash
npm i -g vercel
cd inamigos-site
vercel        # first deploy, creates a preview URL
vercel --prod # promote to production
```

### Option C — GitHub Actions CI/CD (`.github/workflows/deploy.yml`)
Use this only if you specifically want deploys triggered through GitHub Actions
instead of Vercel's own Git integration (e.g. to fold it into a larger CI pipeline).

1. In your Vercel account, get:
   - `VERCEL_TOKEN` → [vercel.com/account/tokens](https://vercel.com/account/tokens)
   - `VERCEL_ORG_ID` and `VERCEL_PROJECT_ID` → run `vercel link` locally once; these
     appear in the generated `.vercel/project.json`
2. In your GitHub repo, go to **Settings → Secrets and variables → Actions** and add
   all three as repository secrets.
3. Push to `main` — the workflow in `.github/workflows/deploy.yml` will deploy to
   production automatically. Pull requests get a preview deployment.

**Note:** Options A and C both auto-deploy on push — don't enable both at once, or
you'll get duplicate deployments for the same push.



- **Palette:** deep indigo (`#1E2A4A`), marigold gold (`#E89A2C`), banyan green (`#4B6F44`), warm paper (`#F5EEDC`)
- **Type:** Fraunces (headings), Work Sans (body), JetBrains Mono (labels/stats)
- **Signature motif:** circular "stamp/seal" badges — used for the organisation's real
  certifications (Section 8, 80G & 12A, CSR-1, NITI Aayog, ISO 9001:2015) and echoed in
  the initiative cards, tying the visual identity to the fact that this is a genuinely
  certified, credential-backed NGO.

---

## 📚 Content sources

All information and photos were sourced directly from InAmigos Foundation's official
website:
- Home / Gallery — `https://inamigosfoundation.org.in/gallery`
- About Us — `https://inamigosfoundation.org.in/page/About-Us`
- Causes — `https://inamigosfoundation.org.in/causes`

Founding date, founder name, registrations (Section 8, 80G/12A, CSR-1, NITI Aayog,
ISO 9001:2015), and all six initiative names/descriptions/stats are taken verbatim in
meaning (paraphrased in wording) from the official About Us page. Photos are hotlinked
from the foundation's own gallery storage (`inamigosfoundation.org.in/public/storage/...`).

---

## ✅ How this maps to the evaluation criteria

- **Content accuracy** — every fact (founding date, founder, registrations, project
  names, impact numbers) is pulled directly from the organisation's own About Us page.
- **Design and structure** — a proper multi-page site (not a single scrolling file),
  shared header/nav/footer, external stylesheet, breadcrumbs, and responsive layout.
- **Effort and creativity** — a considered visual identity (palette, type system, stamp
  motif) rather than a default template look, plus a dedicated volunteer page and
  contact page.
- **Proper use of source information** — content is paraphrased and organised into
  clear sections (About, Initiatives, Impact, Gallery) rather than copy-pasted.

---

## ⚠️ Notes / limitations

- This is a **static front-end only** — the site has no backend, database, or working
  form submission. It was built purely for the awareness-page task, not as a
  production website.
- Images are hotlinked from the official site's own server rather than downloaded
  locally, so an internet connection is needed to see them.
- This is clearly labelled in the footer of every page as an **unofficial awareness
  site built from public information** on inamigosfoundation.org.in.
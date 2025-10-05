# Make IT

**Turn your LinkedIn + GitHub into a polished portfolio — fast.**
A no-code portfolio builder that imports your public LinkedIn & GitHub info, helps you edit it in-browser, and publishes a professional site (Vercel or custom domain) with a single click.

---

## Table of contents

1. [About](#about)
2. [Features](#features)
3. [Tech stack (suggested)](#tech-stack-suggested)
4. [Demo / Screenshots](#demo--screenshots)
5. [Getting started (quickstart)](#getting-started-quickstart)
6. [Repository layout](#repository-layout)
7. [Project `.md` format for GitHub projects](#project-md-format-for-github-projects)
8. [How it works (high level)](#how-it-works-high-level)
9. [Customization & editing](#customization--editing)
10. [Deployment (Vercel)](#deployment-vercel)
11. [Security & privacy](#security--privacy)
12. [Contributing](#contributing)
13. [Roadmap (short)](#roadmap-short)
14. [Troubleshooting / FAQ](#troubleshooting--faq)

---

## About

**Make IT** is a portfolio *builder*, not an auto-updating feed. It imports profile data to bootstrap a portfolio you can edit visually. Think: one-click setup + drag-and-drop polish = recruiter-ready site in minutes.

Why this exists: building a neat portfolio takes time; Make IT gets you from `LinkedIn + GitHub` → `beautiful public portfolio` without code or deployment pain.

---

## Features

* Import public LinkedIn & GitHub data (profile summary, experience, skills, repos).
* Visual, no-code editor (drag-and-drop blocks, edit text, reorder projects).
* Project cards with title, summary, tech stack, and links.
* One-click deploy to Vercel or export for custom domain.
* Templates & theme presets (minimal, developer, creative).
* Basic SEO & automatic SSL (when hosted on Vercel).
* Privacy controls: disconnect, delete portfolio, and selectively hide projects.

---

## Tech stack (suggested)

* Frontend: React (Vite / Next.js) + Tailwind CSS
* Backend: Node.js + Express or Next.js API routes
* Database: PostgreSQL / MongoDB (optional for user accounts)
* Auth & Integrations: OAuth 2.0 (GitHub, LinkedIn)
* Hosting: Vercel (recommended)
* Optional: Prisma / TypeORM for DB, Redis for caching

---

## Screenshots

> Add screenshots / live demo link here once available.


---

## Getting started (quickstart)

### Prerequisites

* Node.js 18+
* Yarn or npm
* GitHub account (for testing GitHub import)
* LinkedIn account (for testing LinkedIn import)

### Quick local run

```bash
# clone
git clone https://github.com/your-org/make-it.git
cd make-it

# install
npm install

# env: create .env from .env.example and set:
#   - GITHUB_CLIENT_ID, GITHUB_CLIENT_SECRET
#   - LINKEDIN_CLIENT_ID, LINKEDIN_CLIENT_SECRET
#   - NEXTAUTH_URL (or your auth base URL)
#   - DATABASE_URL (if using a DB)

# dev
npm run dev
```

Open `http://localhost:3000` (or whatever port your framework uses).

---

## Repository layout

```
/ (root)
├─ /apps (frontend, admin)
├─ /packages (shared ui, utils)
├─ /api (integration endpoints)
├─ /scripts
├─ .env.example
├─ README.md
```

> Keep frontend and API logically separated to simplify deployment (Next.js works well for unified apps).

---

## Project `.md` format for GitHub projects

To make project importing predictable, encourage these fields in each repo (a markdown file like `PROJECT.md` or inside `README.md`):

```md
# Project Title
Short description (1-2 lines)

## Summary
Longer summary (what, why, impact)

## Links
- Live: https://...
- Repo: https://...
- Docs: https://...

## Tech-Stack
- React, Node.js, MongoDB

## Screenshots
- screenshot1.png
```

The importer will:

* Find files named `PROJECT.md` or scan `README.md` for a top-level project block.
* Parse fields (title, summary, links, tech-stack).
* Use them to populate project cards.

---

## How it works (high level)

1. User connects accounts via OAuth (GitHub + LinkedIn).
2. Server fetches public profile and repo metadata.
3. Importer ranks repos (stars, recent activity) and looks for `PROJECT.md` or README content.
4. Create portfolio draft (pre-populated sections).
5. User edits in the visual editor and hits **Publish**.
6. System builds static site and deploys to Vercel, or exports the build for manual hosting.

---

## Customization & editing

* Sections: About, Experience, Projects, Skills, Contact.
* Blocks: Project card, Text block, Image, Tech badges.
* Themes: Light/Dark + color accents.
* Export: Static HTML/CSS bundle or direct Vercel integration.
* Accessibility: semantic HTML, keyboard navigation, alt text prompts for images.

---

## Deployment (Vercel)

1. Create a Vercel account and connect the GitHub repo.
2. Set environment variables in Vercel (same vars as `.env`).
3. Set build command: `npm run build` and output dir (for Next.js, leave default).
4. Add automatic deploy on push (recommended).
5. For custom domains: add domain in Vercel dashboard and configure DNS.

---

## Security & privacy

* OAuth 2.0 for all third-party integrations — no passwords stored.
* Only request the minimum scopes required (public profile, repo metadata).
* All traffic over HTTPS.
* Users may disconnect GitHub/LinkedIn and request full data deletion.
* Follow secure coding practices and periodically audit dependencies.

---

## Contributing

We 💖 contributions. To contribute:

1. Fork the repo.
2. Create a feature branch: `git checkout -b feat/your-feature`.
3. Commit changes: `git commit -m "feat: do X"`.
4. Push: `git push origin feat/your-feature`.
5. Open a PR describing the change and any testing instructions.

Please follow the code style, add tests for features, and keep PRs focused.

---

## Roadmap (short)

* More templates & granular layout control.
* Import from LinkedIn experience as structured entries.
* Add PDF resume export.
* Allow private portfolios (share-by-link).
* Templates optimized for specific roles (SWE, Data, UX).

---

## Troubleshooting / FAQ

**Q: GitHub import failed — repo not found**
A: Ensure repo is public or the OAuth scopes include private repo access.

**Q: LinkedIn import incomplete**
A: LinkedIn API limits fields — fallback to manual editing in the builder.

---

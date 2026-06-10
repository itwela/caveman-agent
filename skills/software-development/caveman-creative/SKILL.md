---
name: caveman-creative-site
description: "Full context for the Caveman Creative HQ website — stack, repo, workflow, and coding standards."
version: 1.0.0
author: itwela
license: MIT
platforms: [linux]
metadata:
  hermes:
    tags: [caveman-creative, nextjs, convex, tailwind, site, itwela]
    related_skills: [github-auth, github-pr-workflow, github-repo-management]
---

# Caveman Creative HQ — Site Agent Context

You are the dedicated agent for the Caveman Creative HQ website. This is your primary project. When the user gives you a task, your default assumption is that it relates to this repo unless they say otherwise.

---

## Repo

- **GitHub:** `https://github.com/itwela/caveman-creative`
- **Branch:** `main`
- **Deploy:** Vercel (auto-deploy on push to main)
- **Local clone target:** `/opt/data/repos/caveman-creative`

---

## Stack

| Layer | Technology |
|---|---|
| Framework | Next.js 16 (App Router) |
| Backend | Convex (real-time DB + serverless functions) |
| Styling | Tailwind CSS v4 |
| Animation | Framer Motion |
| Language | TypeScript |
| Deploy | Vercel |

---

## Project Structure

```
app/
  page.tsx              — Homepage
  layout.tsx            — Root layout
  globals.css           — Global styles
  providers.tsx         — Convex + other providers
  admin/page.tsx        — Admin dashboard
  intake/[slug]/        — Client intake form (dynamic routes)
    page.tsx
    IntakePageClient.tsx
convex/
  schema.ts             — DB schema
  intake.ts             — Intake form mutations/queries
  waitlist.ts           — Waitlist mutations/queries
public/                 — Static assets
```

---

## Working on the Repo

### First time setup

```bash
# Clone the repo
git clone https://github.com/itwela/caveman-creative.git /opt/data/repos/caveman-creative
cd /opt/data/repos/caveman-creative

# Configure git identity
git config user.name "caveman-agent"
git config user.email "itwela@cavemancreativehq.com"

# Embed the GitHub token in the remote URL so pushes don't prompt
git remote set-url origin https://itwela:${GITHUB_TOKEN}@github.com/itwela/caveman-creative.git
```

### After cloning (subsequent tasks)

```bash
cd /opt/data/repos/caveman-creative
git pull origin main
```

### Making changes

1. Pull latest from main
2. Make file edits using your file tools
3. Commit with a clear message
4. Push directly to main (Vercel auto-deploys)

```bash
git add <specific files>
git commit -m "feat: short description of what changed"
git push origin main
```

Commit message types: `feat`, `fix`, `style`, `refactor`, `content`

### If Convex schema changes

Any changes to `convex/schema.ts` or mutations/queries need to be tested against Convex cloud. The user will handle `npx convex deploy` from their machine — your job is to write the correct code and push it.

---

## Coding Standards

- TypeScript everywhere — no `any` unless unavoidable
- Tailwind for all styling — no inline styles
- Framer Motion for animations
- Keep components in the `app/` directory (co-located with routes)
- Convex functions live in `convex/` only
- No comments unless the why is non-obvious
- No placeholder content — write real copy when asked

---

## Who This Site Is For

Caveman Creative HQ is Itwela's creative agency brand. The site is the public-facing home for the brand — client intake, waitlist, portfolio. Keep the tone: confident, direct, no fluff. The brand identity leans dark and clean with a modern edge.

---

## When User Sends a Task

1. Check if repo is already cloned at `/opt/data/repos/caveman-creative`
2. If not, clone it (one-time setup above)
3. Pull latest: `git pull origin main`
4. Make the changes
5. Commit + push
6. Confirm back to user with what changed and the commit hash

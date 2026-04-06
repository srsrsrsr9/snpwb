# SnapSkill Website

Built with [Astro](https://astro.build). Deployed on Netlify (or Vercel).

---

## Local Development

```bash
npm install
npm run dev        # starts at http://localhost:4321
npm run build      # production build
npm run preview    # preview production build locally
```

---

## How to Edit Content

### ✏️ Editing an existing blog post

All blog posts live in `src/content/blog/` as `.md` files.

Open any file and edit the content below the `---` frontmatter block.

The frontmatter controls metadata:
```yaml
---
title: "Your post title"
description: "One sentence summary shown in cards and SEO"
pubDate: 2025-04-01          # publish date
author: "SnapSkill Team"
category: thought-leadership  # thought-leadership | career | case-study
tags: ["AI", "enterprise"]
draft: false                  # set to true to hide from production
---
```

Everything below the second `---` is your post body in Markdown.

### ✏️ Writing a new blog post

1. Create a new file in `src/content/blog/` — e.g. `my-new-post.md`
2. Copy the frontmatter block above and fill it in
3. Write your content in Markdown below it
4. Set `draft: false` when ready to publish

**The filename becomes the URL slug:**
`src/content/blog/my-new-post.md` → `snapskill.in/blog/my-new-post`

### ✏️ Editing navigation links

Open `src/components/Nav.astro` — the links array is at the top of the file:
```js
const navLinks = [
  { label: 'Services', href: '/services' },
  // add or edit entries here
]
```

### ✏️ Editing footer links

Same pattern in `src/components/Footer.astro`.

### ✏️ Changing brand colours or fonts

Everything is in `src/styles/global.css` under `:root { ... }`.
Change once, updates everywhere.

---

## GitHub Workflow (Edit Without Cloning)

You can edit blog posts directly in the GitHub web UI:

1. Go to your repo on github.com
2. Navigate to `src/content/blog/`
3. Click any `.md` file → click the ✏️ pencil icon (top right)
4. Edit → click **Commit changes**
5. Netlify/Vercel auto-deploys within ~60 seconds

**For new posts:**
- In GitHub, go to `src/content/blog/`
- Click **Add file → Create new file**
- Name it `your-post-slug.md`
- Paste your frontmatter + content
- Commit

---

## Deployment (Netlify)

1. Push this repo to GitHub
2. Go to [netlify.com](https://netlify.com) → **Add new site → Import from Git**
3. Select your repo
4. Build command: `npm run build`
5. Publish directory: `dist`
6. Click **Deploy**

Every `git push` to `main` triggers an automatic redeploy.

---

## Project Structure

```
snapskill-site/
├── src/
│   ├── content/
│   │   ├── config.ts          ← schema for blog posts (don't touch often)
│   │   └── blog/
│   │       └── *.md           ← YOUR BLOG POSTS LIVE HERE
│   ├── pages/
│   │   ├── index.astro        ← Homepage
│   │   └── blog/
│   │       ├── index.astro    ← Blog listing page
│   │       └── [...slug].astro ← Individual post template
│   ├── layouts/
│   │   └── BaseLayout.astro   ← HTML shell, SEO meta
│   ├── components/
│   │   ├── Nav.astro          ← Navigation
│   │   └── Footer.astro       ← Footer
│   └── styles/
│       └── global.css         ← Brand tokens, typography, utilities
├── astro.config.mjs
└── package.json
```

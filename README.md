# marvinrose.dev

Personal blog of Marvin Rose — Microsoft Sentinel, Defender XDR, Entra ID and KQL.
Built with [Hugo](https://gohugo.io/) and the [Blowfish](https://blowfish.page/) theme, deployed to GitHub Pages.

## Run locally

```bash
# Hugo extended 0.164–0.167 (Blowfish v3.9.0 range)
brew install hugo            # macOS — check `hugo version`
git clone --recurse-submodules <repo-url>
cd marvinrose.dev
hugo server -D               # http://localhost:1313, -D shows drafts
```

## Write a post

```bash
hugo new content posts/my-post-slug/index.md
```

Front matter used here:

```yaml
title: "..."
date: 2026-11-01
draft: true            # set to false to publish
description: "..."     # SEO + social preview
summary: "..."         # shown on cards
tags: ["Microsoft Sentinel", "KQL"]
categories: ["Microsoft Sentinel"]
series: ["Sentinel Cost Control"]   # optional
series_order: 2              # optional
```

Titles and headings use **sentence case** (capitalise the first word, the first word after a colon, and product names like Conditional Access).

Put images next to `index.md`; a file called `featured.png` becomes the post's hero/social image.
Use ```` ```kql ```` for KQL code blocks.

## Add a talk

Add an entry at the top of `data/talks.yaml`. It shows up on `/talks/` and the newest one on the homepage.
This file doubles as your MVP contribution log.

## Structure

| Path | What |
|---|---|
| `config/_default/` | Site, menu, author and theme settings |
| `assets/css/schemes/graphite.css` | Colour scheme: graphite + violet accent. Switch accent with `python3 scripts/mkscheme.py violet\|orange\|rose` |
| `assets/css/custom.css` | Homepage, talks and small style tweaks |
| `layouts/index.html` | Homepage order: intro → recent posts → latest talk |
| `layouts/partials/home/custom.html` | Homepage intro (name, KQL "whoami" card, topics) |
| `layouts/shortcodes/talks.html` | Renders `data/talks.yaml` |
| `content/` | Posts, About, Talks, Projects, Imprint, Privacy |
| `.github/workflows/hugo.yml` | Build + deploy to GitHub Pages |

## Go live (GitHub Pages + netcup)

1. **Repo visibility:** GitHub Pages on a free account needs a **public** repo. Develop privately, flip to public when ready (or use GitHub Pro).
2. **Settings → Pages → Source:** "GitHub Actions". Every merge to `main` deploys automatically.
3. **Settings → Pages → Custom domain:** `marvinrose.dev`, then tick **Enforce HTTPS** (.dev requires HTTPS).
4. **DNS at netcup** (CCP → Domains → DNS):

   | Host | Type | Value |
   |---|---|---|
   | @ | A | 185.199.108.153 |
   | @ | A | 185.199.109.153 |
   | @ | A | 185.199.110.153 |
   | @ | A | 185.199.111.153 |
   | @ | AAAA | 2606:50c0:8000::153 |
   | @ | AAAA | 2606:50c0:8001::153 |
   | @ | AAAA | 2606:50c0:8002::153 |
   | @ | AAAA | 2606:50c0:8003::153 |
   | www | CNAME | marvin-rse.github.io. |

5. **Verify the domain** (account Settings → Pages → Add a verified domain) and add the TXT record GitHub gives you. Prevents domain takeover.

## Before going live

- [x] Legal Disclosure and Privacy Policy
- [x] Profile photo
- [x] Project links
- [ ] Write and publish the first post (via pull request, `draft: false`)
- [ ] Confirm Umami EU region and DPA
- [x] Verify domain, DNS at netcup, Pages enabled
- [ ] Custom domain in repo settings → Enforce HTTPS

Privacy: no cookies, no external fonts or CDNs. Page views are counted with cookieless Umami Cloud (EU), only in production builds — config in `config/_default/params.toml` → `[umamiAnalytics]`.

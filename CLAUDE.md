# CLAUDE.md — Bible Truth Foundations, Life Arise Ministry Version

## What this folder is

This folder holds a Life Arise Ministry-branded replica of the "Bible Truth Foundations" (BTF) Part 1 course, a 16-lesson Bible study course originally produced for The Well Shrewsbury. Life Arise Ministry saw the original course and asked for an identical copy for their own congregation, published on their own domain.

**Content rule: everything stays the same except attribution and branding.** No teaching content, structure, scripture references, or wording is to be altered. Only two things change from the original:

1. All attribution to "The Well Shrewsbury" → "Life Arise Ministry"
2. Life Arise Ministry's logo is injected into every file (replacing/adding to whatever branding the original had)

## Source of truth

The original BTF Part 1 files live in the parent folder: `G:\My Drive\ROOT-DRIVE\CLAUDE WORK\btf pt1 files\` (one level up from this folder), named `btf-p1-lXX-lesson-name.html`. Any question about "what did the original say" is answered by checking there, not by memory.

## Transformation rules (apply these to replicate this pattern for any future ministry)

1. **Text replacement:** every instance of "The Well Shrewsbury" → "Life Arise Ministry".
2. **Logo injection:** inserted into the first `<div class="title-block">` of each file:
   ```html
   <div class="logo-container">
     <img src="Life Arise Logo.png" alt="Life Arise Ministry Logo" style="max-width:200px; margin-bottom:12px;">
   </div>
   ```
3. **File naming convention:** `btf-lifearise-XX-lesson-name.html` (two-digit lesson number, lowercase, hyphenated). This replaced an earlier, abandoned convention of `btf-lifearise-XX.html` (short form) partway through the project — every file in this folder should now be on the long form. If a short-named duplicate ever resurfaces during a Drive sync, it's leftover from that earlier convention and should be deleted, not treated as current.
4. All internal links in `index.html` must point to the long-form filenames above.

## File manifest (as of last check)

| File | Role |
|---|---|
| `index.html` | Course landing page — logo, intro, accordion "how to use this guide", 16 lesson links grouped into 4 sections (A–D) |
| `btf-lifearise-01-eternal-life.html` – `btf-lifearise-16-the-benefits-of-speaking-in-tongues.html` | The 16 lessons, Life Arise branded |
| `Life Arise Logo.png` | Logo asset referenced by every HTML file |

## Out of scope — the Teacher's Guide

The Teacher's Guide is a standalone teacher-only document that David sends separately. It is deliberately excluded from this folder, the git repo and the public student site — it is not part of this build. Never copy it back in, commit it, or deploy it. A `.gitignore` at the repo root blocks `*Teacher*` / `*Teachers Guide*` patterns as a safety net. (Both previously present Teacher's Guide files were moved out of this folder on 25 Sept 2026.)

**Still not in this folder** (known gap — see status doc):
- `favicon.ico` — referenced by `index.html` (`<link rel="icon" ... href="favicon.ico">`) but not present in this folder. Broken favicon reference, cosmetic only.
- The Teacher's Guide — out of scope by design (see "Out of scope" above), not a gap.

## Deployment

**Current plan (live):** this folder becomes a GitHub repository. Dave edits and commits via the Cline extension in VS Code; Cloudflare Pages is connected to the GitHub repo and auto-deploys on every push to the main branch. No manual drag-and-drop step — a commit is the deploy.

**Repo structure:** this folder (`btf-life-arise-version`) is the repo root. `index.html` at the root is the site's home page; the 16 lesson files sit alongside it, matching the flat structure the existing internal links already expect (no subfolders — changing that would break every `href` in `index.html`). `Life Arise Logo.png` also stays at root since it's referenced by relative path from every HTML file. The Teacher's Guide is not part of the repo (see Out of scope above).

**Setup steps, in order, when Dave is ready:**
1. ~~Clean up duplicate Teacher's Guide files~~ — **moot 25 Sept 2026:** Teacher's Guide is out of scope (see above); both files were moved out of the folder.
2. Add a `favicon.ico` at root if doing a polish pass at the same time (optional, not blocking).
3. Initialise a git repo in this folder, commit locally.
4. **Pause before pushing** — Dave needs to create the empty GitHub repo first (or confirm `gh` CLI auth if letting the tool push directly), so don't assume the push step can happen unattended.
5. Push to the GitHub repo once it exists.
6. In Cloudflare Pages, create a new project connected to that GitHub repo. Build settings: no build command needed (this is static HTML — set the build command to empty/none and the output directory to `/`). **This is a Cloudflare dashboard step only Dave can do** — no tool can create the Pages project or pick the domain on his behalf.
7. Once Cloudflare Pages is live, decide on a custom domain/subdomain there (Cloudflare's own domain management, not Netlify's) — same idea as the old `lifefoundations.netlify.app` rename, just done in Cloudflare's dashboard instead. Also a dashboard-only step.
8. Retire the Netlify site once Cloudflare is confirmed working, so there's only one live copy to keep in sync.

**Tooling note:** Dave is running this migration via the Cline extension in VS Code, working directly against this folder. Cline read this file successfully in a test run (25 Sept 2026) and produced a plan matching the above — confirms this file is a reliable source of truth for a fresh Cline session or a fresh Claude chat to pick up from. Cline's own scope limits: it can do the file cleanup, git init and local commit, and push once a remote exists, but cannot create the Cloudflare Pages project or configure the domain — those remain manual dashboard actions for Dave.

**Dead / retired:** the Netlify Drop deployment (`lifefoundations.netlify.app`) is being replaced by the above and should be treated as legacy. Don't re-drag files there or treat it as the source of truth going forward — GitHub is the source of truth once the repo exists.

A navy QR code (540×540px PNG, Life Arise brand colour #1F3864) was previously generated pointing at the Netlify URL. It will need regenerating once the new Cloudflare domain is finalised — the old QR code points at a site that is being retired.

## Known technical constraints

- The Google Drive MCP connector can only upload files roughly under 50KB directly (`create_file` with `textContent`). The Teacher's Guide (~188KB) exceeds this and needs manual upload.
- Gzip+base64 workarounds were tried and still exceeded practical limits — don't re-attempt this for large files; just flag them for manual upload.

## Outstanding / to verify

1. **Immediate next step:** git init + local commit in this folder (via Cline), pause before push until the GitHub repo exists.
2. Push to GitHub, then set up the GitHub repo and connect it to Cloudflare Pages (see Deployment steps above) — not yet done as of this update. Dashboard steps (Pages project creation, domain setup) are Dave-only.
3. Regenerate the QR code once the new Cloudflare domain is live — the current one points at the Netlify site, which is being retired.
4. `favicon.ico` is referenced but missing — low priority, cosmetic.

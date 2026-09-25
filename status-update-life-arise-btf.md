# Status Update — Life Arise Ministry BTF Part 1

## What this is

A full replica of the Bible Truth Foundations (BTF) Part 1 course (16 lessons, index page) rebuilt for Life Arise Ministry — same content throughout, attribution changed from "The Well Shrewsbury" to "Life Arise Ministry", and the Life Arise logo added to every file. Full technical detail — transformation rules, file naming convention, source file location, deployment setup steps — lives in `CLAUDE.md` in this same folder. Last updated 25 September 2026. Latest change: the Teacher's Guide was ruled **out of scope** for this build (teacher-only, sent separately, never committed or deployed with the public site); deployment plan switched from Netlify Drop to a GitHub + Cloudflare Pages pipeline (edited via Cline in VS Code); Netlify is now retired/legacy.

## Files in this folder

- `index.html` — course landing page linking to all 16 lessons
- `btf-lifearise-01-eternal-life.html` through `btf-lifearise-16-the-benefits-of-speaking-in-tongues.html` — the 16 lessons
- `Life Arise Logo.png` — logo asset
- `CLAUDE.md` — technical spec, transformation rules and deployment setup steps for this project

Note: the Teacher's Guide is **not** in this folder and must never be added — it is a standalone teacher-only document Dave sends separately (see Decisions made).

## Still open, not urgent

| Item | Why it's open | Key notes | Next review |
|---|---|---|---|
| `favicon.ico` referenced but missing | `index.html` links to a favicon that was never created or included | Cosmetic only, browser tab icon will be blank/broken | Next time the site gets a visual polish pass |

## What to do next

**Thread A — Repo and deployment migration**
- [x] ~~Teacher's Guide in repo~~ — **moot: out of scope.** Both Teacher's Guide files were moved out of the folder by Dave; the Guide is teacher-only and sent separately, never part of this repo or the public site (see Decisions made)
- [x] Create `.gitignore` blocking `*Teacher*` / `*Teachers Guide*` patterns
- [x] Initialise a git repo in this folder and commit locally — done 25 Sept 2026, commit `098252e` on branch `main`, 21 files tracked, identity `David Agyei <david@hiturnmedia.com>` (global git config set)
- [x] Push to GitHub — done 25 Sept 2026. Repo: `https://github.com/Daveflyon/btf-lifearise`, branch `main` tracking `origin/main`, commit `098252e` pushed and verified on the remote (`git ls-remote` match)
- [ ] Connect the GitHub repo to a new Cloudflare Pages project (no build command needed — static HTML, output directory `/`) — dashboard step, Dave only
- [ ] Set up the custom domain/subdomain in Cloudflare's dashboard — dashboard step, Dave only
- [ ] Confirm the Cloudflare-hosted site works end to end (all 16 lesson links), then retire the Netlify site
- [ ] Regenerate the QR code once the new Cloudflare domain is confirmed — the current one points at the Netlify URL, which is being retired

**Thread B — Cosmetic polish (not blocking)**
- [ ] Add a `favicon.ico` to this folder

## Progress

- All 16 lessons rebuilt with Life Arise branding and correct long-form filenames
- `index.html` rebuilt with logo, corrected footnote wording, and all 16 lesson links pointing to the correct filenames
- Site deployed live via Netlify Drop at a custom subdomain, lifefoundations.netlify.app
- QR code generated for the live URL, for use in print/PowerPoint materials

## Decisions made

- File naming convention settled as `btf-lifearise-XX-lesson-name.html` (long form), superseding an earlier short-form attempt (`btf-lifearise-XX.html`)
- Content is to remain word-for-word identical to the original BTF Part 1 course; only attribution and logo change
- Deployment method switched from manual Netlify Drop to a git-connected pipeline: GitHub repo, edited via Cline in VS Code, auto-deployed by Cloudflare Pages on push. Netlify is retired.
- This folder (`btf-life-arise-version`) is the repo root; flat structure preserved (no subfolders) since existing internal links assume it
- **The Teacher's Guide is out of scope for this build (25 Sept 2026):** it is a standalone teacher-only document that Dave sends separately, and must never be committed to this repo or deployed with the public student site. A `.gitignore` blocks `*Teacher*` / `*Teachers Guide*` patterns as a safety net.

## Risks or blockers

- GitHub repo and Cloudflare Pages project not yet created — the new pipeline is planned but not live as of this update; Netlify is still the only live copy until the migration is done
- Large files (anything over roughly 50KB) cannot be uploaded to Drive via the MCP connector and need manual handling

## Decisions made — addendum

- ~~Duplicate Teacher's Guide resolved~~ — superseded 25 Sept 2026: the Teacher's Guide is **out of scope** for this build entirely (see Decisions made). Both files were moved out of the folder; it is never committed or deployed with the student site.

## Historical log

- 2026-06-05 to 2026-06-06 — Built all 16 Life Arise lesson files from the BTF Part 1 originals, uploaded to Google Drive "Life Arise Version" folder.
- 2026-06-06 — Built `index.html` with logo, intro copy and lesson links; corrected a footnote ("please" → "please contact"); built the Teacher's Guide from Dave's uploaded original, verified all transformation checks passed, and handed off for manual Drive upload since it exceeded the direct-upload size limit.
- 2026-06-06 (later) — Discovered `index.html` lesson links were still pointing at the old `btf-p1-lXX-name.html` naming instead of the new `btf-lifearise-XX-name.html` convention; fixed all 16 links, fixed a lesson-badge display bug (L15 row was showing "L14"), fixed a stray character in the L01 badge, and re-uploaded the corrected `index.html` to Drive (this required a second upload after Dave found and deleted an older duplicate that had been left in the Drive folder).
- 2026-06-06 (Netlify) — Site deployed via Netlify Drop; initial auto-generated subdomain renamed to `lifefoundations.netlify.app`. A navy QR code (540×540px PNG) was generated for the live URL for use in print materials.
- 2026-09-19 — `CLAUDE.md` and this status document created to consolidate project history and technical detail into one place, since the project had been running across multiple sessions without either.
- 2026-09-19 (later) — Dave confirmed the Teacher's Guide has been added; content spot-checked (Life Arise branding present, no "Well Shrewsbury" references, all 16 lessons and quick reference table intact). Removed as an open item from both this file and CLAUDE.md.
- 2026-09-25 — Full folder contents re-surveyed (parent folder and subfolder both now accessible). Found a duplicate Teacher's Guide file left over from the earlier upload (`Bible Truth Foundation Pt1 - Teachers Guide.html` and `btf-lifearise-00-Teachers-Guide.html`). Dave confirmed the Netlify Drop deployment is being retired in favour of a GitHub + Cloudflare Pages pipeline, edited via the Cline extension in VS Code. CLAUDE.md and this status doc both updated with the new deployment plan, repo structure and setup steps.
- 2026-09-25 (later) — Dave test-drove Cline against this folder: it read `CLAUDE.md` correctly and produced a migration plan matching the documented steps, confirming the file is a reliable handoff point. In doing so, the two duplicate Teacher's Guide files were found to NOT be byte-identical (183.3 KB vs 183.5 KB) — corrected both docs to say "diff before deleting," not "delete blind." Cline was in Plan mode only; nothing had been changed on disk yet at that point.
- 2026-09-25 (later still) — Diffed the two Teacher's Guide files directly. Only differences were the intended rebrand transformation (title, logo injection, series-label, five body references to "The Well Shrewsbury" → "Life Arise Ministry"); no content, structure or wording drift. Confirmed `btf-lifearise-00-Teachers-Guide.html` as correct/current and `Bible Truth Foundation Pt1 - Teachers Guide.html` as the stale unbranded original. Dave deleted the stale file (after one mix-up where the wrong file was deleted first and then corrected). Folder now holds a single, correctly-branded Teacher's Guide. Next: git init, local commit, pause before GitHub push until Dave has created the empty repo (Cline cannot create the Cloudflare Pages project or set the domain — dashboard-only, Dave's side).
- 2026-09-25 (scope change) — Dave ruled the Teacher's Guide **out of scope for this build**: it is a standalone teacher-only document sent separately, and must never be committed to the repo or deployed with the public student site. Both Teacher's Guide files were removed from the folder by Dave (verified gone). Confirmed no "Teacher's Guide" references exist in `index.html` or any of the 16 lesson files (only scripture uses of the word "teacher", left untouched per the content rule). CLAUDE.md and this status doc updated with the out-of-scope decision; `.gitignore` created at the repo root blocking `*Teacher*` / `*Teachers Guide*` patterns; git repo initialised in this folder, first commit pending Dave's confirmation of the file list.
- 2026-09-25 (push) — Git identity set globally to `David Agyei <david@hiturnmedia.com>`; first commit amended to carry it, branch renamed `master` → `main`. Pushed to Dave's new GitHub repo `https://github.com/Daveflyon/btf-lifearise` — `main` tracking `origin/main`, commit `098252e` verified on the remote. Next: Dave sets up the Cloudflare Pages project + custom domain (dashboard-only), then the Netlify site is retired and the QR code regenerated.

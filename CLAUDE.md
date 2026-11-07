# CLAUDE.md — elizeng.github.io

Personal academic website for **Elize Ng** (Postdoctoral Research Fellow, University of Queensland).
Built with **Hugo + Hugo Blox (Academic CV template, `blox-tailwind`)**, deployed to **GitHub Pages** at https://elizeng.github.io.

## Ground rules

1. **Content accuracy comes first.** Never invent publications, co-authors, dates, DOIs, venues, awards, or job titles. If a detail is unknown, leave the field empty (`''`) and flag it to the user — don't guess.
2. **Source of truth for CV facts:** `../Documents/Elize Ng_CV_Oct2026_updated.docx` (the folder above this repo). When updating publications, talks, experience, or education, check against it and list any discrepancies rather than silently picking one.
3. **Ask before deleting** existing content pages or images. Demo/template leftovers (see below) may be removed, but confirm the list with the user first.
4. **Smallest change that works.** Edit content and config; don't fork or override theme templates in `layouts/` unless a YAML/front-matter option genuinely can't do it.
5. **Don't change the build stack** (Hugo version `0.136.5`, Hugo Blox module versions in `go.mod`, GitHub Actions workflows) unless the user asks. If you do, update the version in *all* of `hugoblox.yaml`, `netlify.toml`, and `.github/workflows/publish.yaml` together.
6. **No commits or pushes without being asked.** Pushing to `main` publishes the live site immediately.
7. **Preserve UTF-8.** Files contain emoji (e.g. section titles on the homepage) and may contain accented author names. Edit with the Edit/Write tools; don't rewrite files via PowerShell `Set-Content`/`Out-File`, which re-encodes them.
8. **Privacy:** only use contact details already on the site (`content/authors/admin/_index.md`). Don't add phone numbers, home addresses, or other personal info.

## Project layout

| Path | What it is |
|---|---|
| `config/_default/hugo.yaml` | Site title, base URL, taxonomies |
| `config/_default/params.yaml` | Theme colour/mode, SEO, navbar, footer/copyright |
| `config/_default/menus.yaml` | Top navigation links |
| `content/_index.md` | Homepage — a list of Hugo Blox `sections` (biography, research blurb, publications…) |
| `content/authors/admin/_index.md` | Profile: role, affiliations, social links, interests, education, experience, skills, awards. Feeds the bio and `/experience/` page |
| `content/publication/<slug>/index.md` | One folder per paper |
| `content/event/<slug>/index.md` | Talks / conference presentations |
| `content/project/<slug>/index.md` | Research projects (shown on `/projects/`) |
| `content/teaching/_index.md` | Teaching page (single Markdown block, grouped by institution) |
| `content/experience.md` | Experience page; includes a "Service & Memberships" Markdown block |
| `assets/media/` | Images processed by Hugo (backgrounds, icons in `assets/media/icons/`) |
| `static/uploads/resume.pdf` | CV linked from the "Download CV" button |
| `.github/workflows/publish.yaml` | Builds and deploys on push to `main` |
| `.github/workflows/import-publications.yml` | Converts a root `publications.bib` into publication pages via PR |

## Content conventions

### Publications (`content/publication/<slug>/index.md`)
- Folder slug: lowercase, hyphenated title, truncated to ~60 characters (matches existing folders).
- `authors:` — use `admin` for Elize; other authors as full names in published order.
- `date:` — **year only**. Always write `"YYYY-01-01T00:00:00Z"` (Hugo needs a full date, but only the year is meaningful). Never use the real month/day, even if known.
- `publication:` — journal in Markdown italics, e.g. `"*Ecography*"`. For unpublished work append the status: `(in submission)`, `(in review)`, `(in press)`.
- `publication_types:` — `["article-journal"]` for published papers, `["manuscript"]` for in-prep/submitted, `["paper-conference"]`, `["chapter"]`, `["book"]`, `["report"]` as appropriate.
- Fill `doi:` (bare DOI, no `https://doi.org/`) and `url_pdf`/`url_code`/`url_dataset` when known; leave others `''`.
- `featured: true` only for papers the user wants in the homepage "Featured Publications" grid.
- When a manuscript gets published, update the existing page (journal, date, DOI, type) — don't create a duplicate.
- Bulk alternative: put a `publications.bib` at repo root and push; the import workflow opens a PR.

### Talks (`content/event/<slug>/index.md`)
- Required: `title`, `event`, `date` (and `date_end` for multi-day), `authors: [admin]`, one-line `summary`.
- Fill `location` and `event_url` when known.

### Projects (`content/project/<slug>/index.md`)
- `title`, `date`, one-sentence `summary`, a few `tags`, then a short paragraph and `<!--more-->`.
- Add a `featured.jpg`/`featured.png` in the folder for a card image (only images the user supplies or owns the rights to).

### Profile (`content/authors/admin/_index.md`)
- Keep `role` and `organizations` in sync with the CV. Experience/education entries use `date_start`/`date_end` in `YYYY-MM-DD`; omit `date_end` for current roles.

### Writing style
- Australian/British spelling (e.g. "organisation", "behaviour") to match existing text.
- Third person or first person consistently per section — follow what's already there.
- Plain, concise, accessible to a non-specialist; species names in italics where used in prose.

## Template leftovers
Removed in the November 2026 rebuild (demo posts, demo courses, demo talk, homepage advert block, News menu link, GitHub star-button script, template README). Don't reintroduce Hugo Blox demo content. Homepage menu anchors must match a section `id` in `content/_index.md` (`papers`, `talks`).

## Building & checking

Hugo is **not installed system-wide** on this machine. Options:
- Install Hugo **extended** `0.136.5` (plus Go, needed for Hugo Modules), then run `hugo server` from this folder and open http://localhost:1313.
- Or push to a non-`main` branch / check the GitHub Actions build log after a push to `main`.

Before handing work back, at minimum:
- Validate YAML front matter (matching `---` fences, consistent indentation, quoted strings containing `:` or `*`).
- Check every new page has a unique folder slug and a valid date.
- Confirm referenced files exist (images, `uploads/resume.pdf`, icons).
- Summarise what changed and list anything left blank or needing the user's input.

## Environment notes
- The project lives in a OneDrive-synced folder on Windows; build into a folder outside OneDrive (e.g. `hugo -d <temp dir>`) rather than creating `public/`/`resources/` here. Both are in `.gitignore`.
- This folder is not yet a git repository. To publish, `git init` it and connect it to `github.com/elizeng/elizeng.github.io`, or copy its contents into a clone of that repo.
- `static/uploads/resume.pdf` is exported from the CV `.docx`; re-export it whenever the CV changes.

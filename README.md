# lourdes-romao

Portfolio site for **Lourdes Romão** — visual artist, graphic designer,
photographer, sculptor and glass artist.

Static HTML/CSS/JS — **no build step**. Edit and push; GitHub Pages serves it directly.

## Structure

| Path | Purpose |
|------|---------|
| `index.html` | The whole site: hero, art gallery (with lightbox), about, footer. |
| `styles.css` | Dark editorial theme (Cormorant Garamond + Montserrat, gold accent). |
| `assets/art.js` | **The artwork catalogue** — add/remove/reorder pieces here. |
| `assets/art/` | Artwork images (26). |
| `assets/lourdes.jpg` | Hero portrait. |
| `assets/favicon.svg` | Site favicon. |
| `assets/particleprismatics-mark.svg` | Studio mark used in the nav link. |
| `.nojekyll` | Serve files as-is (skip Jekyll processing). |

**All paths are relative** (`assets/...`, not `/assets/...`) so the site works
unchanged whether it's served from a project subpath
(`particleprismatics.github.io/lourdes-romao/`) or from a domain root.
Keep it that way — root-absolute paths will break the project-page deployment.

## Adding artwork

1. Drop the image in `assets/art/` (use a lowercase, hyphenated filename — no spaces).
2. Add an entry to the right category in `assets/art.js`:

```js
{ "src": "assets/art/glass-new-piece.jpg", "title": "New Piece", "year": "2026", "medium": "Fused glass" }
```

`year` may be an empty string. Categories are `Paintings`, `Sculptures`, `Glass Work`.

## Local preview

```bash
python -m http.server 8000
```

Then open http://localhost:8000. (Opening `index.html` directly by double-click
also works — the catalogue is a plain script, not a `fetch`.)

## Deploy — GitHub Pages under the Particle Prismatics org

1. Create the repo `particleprismatics/lourdes-romao`.
2. Push this directory to the default branch.
3. **Settings → Pages → Source:** deploy from branch, root (`/`).
4. It serves at **https://particleprismatics.github.io/lourdes-romao/**

### Optional: a custom domain
- **Own domain** (e.g. `lourdesromao.com`): add a `CNAME` file containing the
  domain, point the apex at the GitHub Pages IPs
  (`185.199.108–111.153`) with four `A` records, then enable **Enforce HTTPS**.
- **Subdomain of particleprismatics.com** (e.g. `lourdes.particleprismatics.com`):
  add a `CNAME` file with that hostname, and a DNS `CNAME` record
  `lourdes` → `particleprismatics.github.io`.

Because all paths are relative, no code changes are needed when moving between
the project subpath and a custom domain.

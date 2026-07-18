# openchronicles.org

Static public site for **Open Chronicles** (https://openchronicles.org).

## Stack

- Plain HTML + CSS (no framework, no build step)
- GitHub Pages from the repository root (`master` branch)
- Custom domain: `openchronicles.org` (see `CNAME`, `DNS.md`)

## Local preview

```bash
python -m http.server 8080
```

Open http://localhost:8080

## Public pages

| File | Role |
|------|------|
| `index.html` | Home |
| `library.html` | Library (published + in-preparation works) |
| `method.html` | Editorial method |
| `license.html` | CC BY 4.0 |
| `about.html` | About |
| `corrections.html` | Errata log and how to report errors |
| `books/tudebode/` | Volume 1 landing page |
| `books/tudebode/the-journey-to-jerusalem.html` | Source-faithful browser edition |
| `books/tudebode/the-road-to-jerusalem.html` | Reader’s browser edition |
| `404.html` | Custom not-found page (GitHub Pages) |

`branding.html` is an internal brand archive and is not listed in `sitemap.xml`.

## Publication files

PDFs for Tudebode live beside the HTML editions under `books/tudebode/`. Do not edit translation body text in the HTML editions or rebuild binary PDFs from this site cleanup workflow unless a separate, documented generation process is used.

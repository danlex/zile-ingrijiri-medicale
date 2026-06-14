# zile-ingrijiri-medicale.ro

Single-page Jekyll site for **Cabinet de Avocat VARZARU ION**, recreating the content of
`zile-ingrijiri-medicale.ro` with a modern template (shared with `avocat-asigurari-rca.ro`).
Deployed on GitHub Pages at the custom domain **zile-ingrijiri-medicale.ro**.

## Structure

```
.
├── index.html               # Single page — assembles the section includes
├── _layouts/default.html    # HTML shell (head, header, footer)
├── _includes/               # Page sections
│   ├── header.html  footer.html
│   ├── hero.html  despre-cabinet.html  zile.html
│   ├── despre.html  intrebari.html  testimoniale.html  contact.html
│   └── structured-data.html
├── assets/css/style.scss    # Theme (compiled to style.css by Jekyll)
├── content/                 # Source content parsed from the original site (excluded from build)
├── _config.yml              # Site + contact settings
├── CNAME                    # Custom domain: zile-ingrijiri-medicale.ro
└── .github/workflows/jekyll.yml   # Build + deploy to GitHub Pages
```

Editable content lives in the `_includes/*.html` section files. Contact details (phone, email, name,
address) are centralized in `_config.yml` under `contact:` and pulled in via `{{ site.contact.* }}`.

## Local preview

```bash
bundle install
bundle exec jekyll serve --livereload
# open http://localhost:4000
```

## Deploy (GitHub Pages)

1. Create a repo and push these files to the `main` branch.
2. In **Settings → Pages → Build and deployment**, set **Source = GitHub Actions**.
   (The included `.github/workflows/jekyll.yml` builds and deploys on every push to `main`.)
3. The `CNAME` file sets the custom domain to `zile-ingrijiri-medicale.ro`. In **Settings → Pages**
   confirm the custom domain and enable **Enforce HTTPS** once the certificate is issued.

## DNS (point the domain at GitHub Pages)

- **Apex `zile-ingrijiri-medicale.ro`** → four `A` records:
  `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
  (optionally the `AAAA` records: `2606:50c0:8000::153` … `8003::153`)
- **`www`** → `CNAME` to `<your-github-username>.github.io.`

DNS changes can take up to 24h to propagate; the HTTPS certificate is issued automatically afterwards.

## Content note

The original site's testimonials section was an empty placeholder; this rebuild reuses the firm's
real client testimonials (accident-compensation cases). The FAQ pairings reproduce the original site
faithfully, including its content as published.

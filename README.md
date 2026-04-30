# Redwood Revival Press

Static site for [redwoodrevivalpress.com](https://redwoodrevivalpress.com), hosted on GitHub Pages.

## Layout

```
/
├── index.html        # press homepage
├── coffee/
│   └── index.html    # "History of Coffee" — long-form companion
├── CNAME             # redwoodrevivalpress.com
└── README.md
```

Each publication lives at its own subpath (`/coffee/`, future titles get their own directory). The press homepage at `/` lists the catalogue.

## Local preview

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

## Deployment (GitHub Pages, custom domain)

One-time setup, after the GitHub org `redwoodrevivalpress` exists and this repo is pushed there:

1. **Repo settings → Pages** — set source to `main` branch, root.
2. **Repo settings → Pages → Custom domain** — enter `redwoodrevivalpress.com` and tick *Enforce HTTPS* once the cert provisions.
3. **DNS at the registrar for `redwoodrevivalpress.com`** — add the four GitHub Pages A records for the apex plus a CNAME for `www`:

   | Type  | Host  | Value                  |
   |-------|-------|------------------------|
   | A     | @     | 185.199.108.153        |
   | A     | @     | 185.199.109.153        |
   | A     | @     | 185.199.110.153        |
   | A     | @     | 185.199.111.153        |
   | CNAME | www   | redwoodrevivalpress.github.io |

4. Pushes to `main` deploy automatically.

## Updating the coffee dispatch

The `coffee/index.html` here is a copy of `~/Code/coffee-origins/web/index.html`. To re-sync after changes upstream:

```sh
cp ~/Code/coffee-origins/web/index.html ~/Code/redwoodrevivalpress/coffee/index.html
```

Add a make target if this becomes routine.

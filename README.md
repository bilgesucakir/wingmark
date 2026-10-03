# Wingmark site

Public website for the Wingmark iOS app, hosted on GitHub Pages at
https://bilgesucakir.github.io/wingmark/

Every page exists in English and Turkish. A toggle in the header switches between the two versions of the same page.

| English | Turkish | Used for |
|---|---|---|
| `index.html` (`/wingmark/`) | `index-tr.html` | Landing page, App Store marketing URL |
| `privacy.html` | `privacy-tr.html` | Privacy Policy (App Store Connect + in-app link) |
| `support.html` | `support-tr.html` | App Store support URL |
| `404.html` | (same page, both languages) | Not-found page |

Plain HTML with one stylesheet (`style.css`) and a self-hosted font (Literata, SIL OFL, in `fonts/`).
No build step, no trackers, no third-party requests.

## Publishing

Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder `/ (root)`.

Links between pages are relative, except in `404.html`, which uses `/wingmark/...` because GitHub serves it
at any path. Update those links if the site moves to a custom domain.

## Keep in sync with the app

Update both privacy pages (and their "Last updated" date), and any text that changes on a page in both languages, before submitting any app version that changes
what data is collected or who processes it.

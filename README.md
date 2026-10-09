# Wingmark site

Public website for the Wingmark iOS app, hosted on Cloudflare at
https://wingmarkapp.com/

Every page exists in English and Turkish. A toggle in the header switches between the two versions of the same page.

| English | Turkish | Used for |
|---|---|---|
| `/` (`index.html`) | `/index-tr` | Landing page, App Store marketing URL |
| `/privacy` | `/privacy-tr` | Privacy Policy (App Store Connect + in-app link) |
| `/support` | `/support-tr` | App Store support URL |
| `/accessibility` | `/accessibility-tr` | What the app supports for accessibility, and what it does not |
| `404.html` | (same page, both languages) | Not-found page |

Each address is a file of the same name with `.html` in the repository (for example `/privacy` is `privacy.html`).

Plain HTML with one stylesheet (`style.css`) and a self-hosted font (Literata, SIL OFL, in `fonts/`).
No build step, no trackers, no third-party requests.

## Publishing

Hosted on Cloudflare (Workers & Pages), connected to this repository. Every push to `main` deploys.

- `wrangler.jsonc`: publishes the repository root as static assets; the `name` must match the project name in Cloudflare; `not_found_handling` serves `404.html` for unknown addresses.
- `.assetsignore`: files that are in the repository but must not be public (README, config).
- `_headers`: security headers and long caching for the font files.
- No build command is needed. Deploy command: `npx wrangler deploy`.
- Custom domain: Cloudflare project > Settings > Domains & Routes (wingmarkapp.com, and www redirecting to it).

Cloudflare drops the `.html` ending: `/privacy.html` redirects (307) to `/privacy`. Links between pages therefore use the clean root addresses (`/privacy`, `/support`, `/accessibility`, `/index-tr`, and so on; `/` for the English home page), and the `hreflang` tags use full `https://wingmarkapp.com/...` addresses. The site must live at the root of its domain, because `404.html` is served at any address and uses root paths (`/style.css`, `/privacy`).

# LinkedIn Job Search URL Builder

A browser-based tool for building custom LinkedIn job search URLs with bulk company filters and advanced parameters. Skip the tedious one-by-one company dropdown — paste IDs in bulk and go.

**Zero dependencies. Single HTML file. Runs offline. Works on mobile.**

> **100% private** — this tool runs entirely in your browser. No data is sent to any server. No analytics, no cookies, no tracking.

## Why?

LinkedIn's job search lets you filter by company, but adding companies one at a time through the dropdown is painfully slow — especially if you're targeting 20, 50, or 100+ companies in a specific industry.

Under the hood, LinkedIn stores company filters as numeric IDs in the URL parameter `f_C`. This tool lets you:

- **Bulk-add company IDs** instead of selecting them one by one
- **Combine all LinkedIn search parameters** into a single bookmarkable URL
- **Export/import company lists** as JSON to share with others
- **Persist everything in localStorage** so your setup survives browser restarts

## Getting Started

### Option 1: Use online (GitHub Pages)

Visit the live tool — no install required:

```
https://brodiecox.github.io/linkedin-job-tool/
```

### Option 2: Run locally

```bash
git clone https://github.com/brodiecox/linkedin-job-tool.git
open index.html
```

That's it. No build step, no server, no dependencies.

## Features

- Bulk paste comma-separated company IDs
- Add companies individually with optional LinkedIn page links for ID lookup
- Full LinkedIn search parameter support:
  - Keywords
  - Time posted (custom windows down to 1 hour)
  - Location (Geo ID) with common reference values
  - Experience level
  - Job type (full-time, contract, etc.)
  - Workplace type (remote, hybrid, on-site)
  - Sort order
- Export/import company lists as JSON
- Auto-saves all state to localStorage
- Copy URL or open directly in LinkedIn
- Mobile responsive
- Dark theme

## How to Find LinkedIn Company IDs

### Option A: From the company filter (fastest)

1. Go to [LinkedIn Jobs](https://www.linkedin.com/jobs/)
2. Type a company name into the **Company** filter dropdown
3. Select it, then copy the number after `f_C=` in the URL

### Option B: From the company page

1. Visit the company's LinkedIn page
2. Click **"See all jobs"** or **"See all employees"**
3. The ID appears after `f_C=` or `currentCompany=` in the URL

### Option C: Verify an ID

Visit `linkedin.com/company/[ID]` — it redirects to the company page.

## Common Geo IDs

| Location | Geo ID |
|----------|--------|
| Australia | `101452733` |
| United Kingdom | `101165590` |
| United States | `103644278` |
| Canada | `101174742` |
| New Zealand | `102095887` |
| Sydney | `100009818` |
| Melbourne | `103116251` |
| London | `102257491` |
| New York | `102571732` |

Find more by searching LinkedIn Jobs for a location and copying the `geoId=` value from the URL.

## LinkedIn URL Parameters Reference

| Parameter | Description | Example Values |
|-----------|-------------|----------------|
| `keywords` | Search terms | `product manager` |
| `f_C` | Company IDs (comma-separated) | `8900,42797345,1319529` |
| `geoId` | Location | `101452733` (Australia) |
| `f_TPR` | Time posted | `r3600` (1hr), `r7200` (2hr), `r21600` (6hr), `r86400` (24hr), `r604800` (week) |
| `f_E` | Experience level | `1`-`6` (Intern to Executive) |
| `f_JT` | Job type | `F` (full-time), `P` (part-time), `C` (contract) |
| `f_WT` | Workplace type | `1` (on-site), `2` (remote), `3` (hybrid) |
| `sortBy` | Sort order | `DD` (most recent) |

## Sharing Company Lists

Export your company list as JSON and share it with others:

1. Click **Export** to download your list as `linkedin-companies.json`
2. Share the file
3. Others click **Import** to load it into their instance

### JSON format

```json
[
  { "name": "Google", "slug": "google", "id": "1441" },
  { "name": "Atlassian", "slug": "atlassian", "id": "15135" }
]
```

## Deploying Your Own Instance

### GitHub Pages

1. Fork or clone this repo
2. Go to **Settings > Pages**
3. Set source to **Deploy from a branch**, select `main`, root directory `/`
4. Your tool will be live at `https://YOUR_USERNAME.github.io/linkedin-job-tool/`

### Self-hosted

Serve `index.html` from any static file server (Nginx, Caddy, S3, Netlify, Vercel, etc.). No build step required.

## Privacy

This tool runs entirely in your browser. No data is sent to any server. No analytics, no cookies, no tracking. Company lists and search parameters are stored in `localStorage` only.

## License

[MIT](LICENSE) - Brodie Cox

## Disclaimer

This tool is not affiliated with, endorsed by, or connected to LinkedIn or Microsoft Corporation. LinkedIn is a trademark of LinkedIn Corporation.

# Choose A Name

Single-page auction site: submit a name, bid on it, highest bid at the buzzer wins.

- `index.html` — the whole site. No build step, no dependencies beyond Google Fonts.
- `vercel.json` — clean URLs + cache headers for a static deploy.

## Editing

Everything you'll actually want to change lives in one `CONFIG` block at the top
of the `<script>` at the bottom of `index.html`:

| Constant | What it does |
| --- | --- |
| `AUCTION_ENDS` | ISO 8601 timestamp the countdown counts down to. Include a timezone. |
| `BID_URL` | Where every "Make a bid" button points (Telegram, form, mailto). |
| `BIDS` | Leaderboard rows. Sorted by `value` at render time, so order doesn't matter. |

The hero image is a dashed placeholder. Replace the contents of `.hero-art .frame`
with `<img src="hero.jpg" alt="…">` — it's already styled to cover a 3:4 box.

## Run locally

```
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Deploy

Any static host — Vercel, Netlify, GitHub Pages, Cloudflare Pages. Serve
`index.html` at the root. On Vercel: **Add New → Project → import this repo**,
framework **Other**, leave build and output settings empty.

## Notes

- Leaderboard rows are HTML-escaped before rendering.
- All motion (marquee, hovers) is disabled under `prefers-reduced-motion`.
- Layout is responsive; the leaderboard collapses to a stacked card under 900px.
- The leaderboard data shipped here is placeholder content, not real bids.

# Choose A Name

Single-page auction site: submit a name, bid on it, highest bid at the buzzer wins.

- `index.html` — the whole site. No build step, no dependencies beyond Google Fonts.
- `vercel.json` — clean URLs + cache headers for a static deploy.

## Editing

Everything you'll actually want to change lives in one `CONFIG` block at the top
of the `<script>` at the bottom of `index.html`:

| Constant | What it does |
| --- | --- |
| `AUCTION_ENDS` | ISO 8601 timestamp (with timezone) the clock counts down to, or `null`. |
| `COUNTDOWN_MINUTES` | Used only when `AUCTION_ENDS` is `null`. Currently `30`. |
| `BID_URL` | Where every "Make a bid" button points (Telegram, form, mailto). |
| `BIDS` | Leaderboard rows. Sorted by `value` at render time, so order doesn't matter. |

### The countdown

Ships as `AUCTION_ENDS = null`, so the clock starts at `COUNTDOWN_MINUTES` (30)
on every page load and reads `00 : 00 : 30 : 00`.

**That restarts on every refresh, and each visitor gets their own 30 minutes.**
It looks right for a demo, but it is not a real deadline. Before the auction is
live, set `AUCTION_ENDS` to a fixed timestamp so everyone sees the same clock:

```js
const AUCTION_ENDS = '2026-10-01T20:00:00Z';
```

At zero the clock freezes and a "bidding is closed" line appears.

### The hero image

The hero is self-hosted from `assets/bonnie.png`:

```html
<img id="heroImg" src="assets/bonnie.png" alt="Bonnie Blue" />
```

To swap it, drop a new file in `assets/` and update that `src`. If the image fails to load the page falls back to a dashed
placeholder box rather than showing a broken image. See
[`assets/README.md`](assets/README.md) for sizing.

Framing is `object-fit: cover` with `object-position: 50% 12%`, which favours
the top of the image so a head doesn't get cropped. Adjust that percentage in
the `.hero-art img` rule if the crop sits wrong.

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

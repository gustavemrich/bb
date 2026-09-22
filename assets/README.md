# assets

Drop images here. The site picks them up by filename — no build step, no imports.

| File | Used by |
| --- | --- |
| `hero.jpg` | The hero panel on the right of the headline. |

## hero.jpg

- **Aspect ratio:** 3:4 (portrait). Other ratios work — the image is
  `object-fit: cover`, so it crops from the centre rather than squashing.
- **Suggested size:** around 900×1200. Bigger is wasted; smaller goes soft on
  retina screens.
- **Format:** `.jpg` is what the page asks for by default. To use a `.png`,
  `.webp` or `.avif` instead, change the `src` on `#heroImg` in `index.html`.

If `hero.jpg` is missing or fails to load, the page falls back to a dashed
placeholder box automatically — nothing breaks, so it's safe to deploy before
you have the art.

## Adding a file

```
git add assets/hero.jpg
git commit -m "Add hero image"
git push
```

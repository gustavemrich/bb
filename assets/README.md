# assets

Drop images here. The site picks them up by filename — no build step, no imports.

| File | Used by |
| --- | --- |
| `bonnie.png` | The hero panel on the right of the headline. |

## bonnie.png

- **Aspect ratio:** 3:4 (portrait). Other ratios work — the image is
  `object-fit: cover`, so it crops from the centre rather than squashing.
- **Suggested size:** around 900×1200. Bigger is wasted; smaller goes soft on
  retina screens.
- **Format:** any web format works — `.png` keeps transparency, `.jpg` is
  smaller for photos. Whatever you use, match the `src` on `#heroImg`.

If the hero image is missing or fails to load, the page falls back to a dashed
placeholder box automatically — nothing breaks, so it's safe to deploy before
you have the art.

## Adding a file

```
git add assets/bonnie.png
git commit -m "Add hero image"
git push
```

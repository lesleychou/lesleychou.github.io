# blog/

Plain-HTML blog. No build step, no dependencies beyond the Bootstrap + Font Awesome
CDNs the rest of the site already loads.

```
blog/
  index.html      the listing page (card grid)
  template.html   copy this to start a post
  blog.css        all blog styles
```

## Publishing a post

1. `cp template.html 2026-09-13-my-post-slug.html`
2. Edit it. The blocks to fill in are marked with `<!-- ===== ... ===== -->` comments;
   delete any block you don't need (equation, table, references, prev/next are all optional).
3. Open `index.html`, copy the top `<a class="post-card">` block, paste a new one above it,
   and update: `href`, thumbnail `src` + `alt`, kicker (month · read time),
   title, and dek.
4. Commit and push. That's it.

## Post shape (template.html)

Hero (series kicker, question-style title, italic `.post-subtitle`, authors · date ·
read time · tags) → TL;DR bullets → Fig. 1 overview → un-headed intro → sections whose
headings are claims or questions → the "lesson" → `.callout.cta` with the copy-email
button → references (`<em>Title.</em> Venue, Year. Authors. [arXiv] [code]`).
The copy-email button assembles the address on click, so it is never in the HTML.

## Conventions

- **Filenames:** `YYYY-MM-DD-slug.html`. Not required by anything, but it keeps the
  directory sorted and makes the URL self-dating.
- **Thumbnails** live in `../images/`. Cards crop to 16:9 from the top, so a figure with
  its title bar at the top survives the crop best.
- **No figure?** Replace the `<div class="thumb">` with
  `<div class="thumb is-empty" data-label="Essay"></div>` — you get a hatched panel
  instead of a broken card.

## Notes

- `stylesheets/stylesheet.css` is deliberately **not** loaded here. It's the legacy Meyer
  reset from the old site and it overrides `h1`–`h3`, strips list markers, and forces
  Raleway + `text-shadow`. The blog uses Bootstrap + `blog.css` only, and rebuilds the
  navbar/footer with the same Bootstrap classes so they still match `../index.html`.
- Avoid filenames starting with `_` — GitHub Pages runs Jekyll by default on this repo
  and will not serve them.
- If you edit the navbar, edit it in `index.html`, `template.html`, **and** every existing
  post. That duplication is the price of having no build step; it's about 15 lines.

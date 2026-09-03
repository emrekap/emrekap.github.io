# emrekap.github.io

## Deploy

1. Create a public GitHub repository named `emrekap.github.io` (the name must match exactly; the site is served from it).
2. Push this folder to its `main` branch.
3. In the repository, open Settings, then Pages. Under Build and deployment choose Deploy from a branch, pick `main` and `/ (root)`, and save.
4. Wait about a minute. The site is at https://emrekap.github.io.

There is no build step. `.nojekyll` tells GitHub Pages to serve the files as they are.

The same thing from the terminal, run inside this folder:

```sh
gh repo create emrekap.github.io --public --source=. --remote=origin --push
gh api -X POST repos/emrekap/emrekap.github.io/pages -f build_type=legacy -f 'source[branch]=main' -f 'source[path]=/'
```

Optional custom domain: add a file named `CNAME` containing the domain (for example `emrekaplan.dev`), then at the DNS provider point the apex at GitHub Pages' A records (185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153) or a `www` subdomain at `emrekap.github.io` with a CNAME record. Enter the same domain under Settings, Pages, Custom domain, and tick Enforce HTTPS once the certificate is issued.

## Edit

The whole site is `index.html`. Styles are in the `<style>` block at the top; there is no JavaScript.

Where things live, in page order:

- `<head>`: title, meta description, Open Graph and Twitter tags, the inline SVG favicon, the Google Fonts link.
- `<main>` opening: the name, the lede, and the Now / Where / Contact rows.
- `<section id="what">`: What I do, a `<dl>` of label and text pairs.
- `<section id="work">`: Selected work. Nemu (paragraphs, the type-chain `<figure>`, the Measured, Counted, and Detector releases tables), then Resonance and Earlier public work.
- `<section id="ai">`: How I use AI, a `<dl>` like What I do.
- `<section id="experience">`: one `<li class="job">` per job with the date, the company / role / location line, and a paragraph; then Education and Languages.
- `<section id="contact">` and `<footer>`: the contact line and the full contact URLs.

Some facts are still marked with `<!-- CONFIRM: ... -->` comments next to the text they concern. They are invisible on the page. Resolve each one, then delete the comment.

Two fonts settings to know: the name is set in Bricolage Grotesque with `font-stretch: 80%`; if the font fails to load, the `Narrowed` fallback face keeps the name from overflowing a phone screen.

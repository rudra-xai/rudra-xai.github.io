# Rudra-X AI — website

Landing page for Rudra-X AI, live at **https://rudra-xai.github.io**.

It is a plain static site (no build step, no framework). GitHub Pages publishes the `main` branch automatically — every push goes live in about a minute.

## Files

| Path | What it is |
|---|---|
| `index.html` | The whole page: content, styles (in `<style>`) and the animated background (in `<script>`) |
| `assets/rudra-x-ai-logo.png` | Logo used on the site (1400px wide, light version for the dark background) |
| `assets/favicon.svg` | Browser tab icon |
| `brand/` | Original full-size logo files (light and dark versions) |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is |

## Making an edit

**On github.com (no tools needed):** open `index.html`, click the pencil icon, edit, then **Commit changes**.

**On your computer:**

```bash
git pull
# edit index.html, then:
git add -A
git commit -m "Describe the change"
git push
```

To preview locally before pushing, run `npx http-server . -p 5173` in this folder and open http://localhost:5173.

## Where things are in `index.html`

- **Colors and sizes:** the `:root { ... }` block at the top of `<style>` (navy `--bg`, yellow `--yellow`, gold `--gold`).
- **Fonts:** Tektur (headings), Martian Mono (labels/buttons), Inter (body), loaded from Google Fonts.
- **Links:** the Tally form (`https://tally.so/r/zxdbP1`), contact email, and Calendly link — search the file for them to change.
- **Scrolling strip text:** the `<div class="track">` block (the list appears twice so the loop is seamless — edit both).

## Automatic deployment (CI/CD)

`.github/workflows/deploy.yml` runs on every push to `main` (and can be started by hand from the **Actions** tab). It:

1. **Checks** the site — required files exist, every local image/link in `index.html` points to a real file, and the HTML is well-formed.
2. **Deploys** to GitHub Pages only if the checks pass. If a check fails, the live site stays as it was and the failing step in the Actions tab says what's wrong.

Only `index.html`, `assets/` and `.nojekyll` are published; `README.md`, `brand/` and `.github/` stay in the repo only.

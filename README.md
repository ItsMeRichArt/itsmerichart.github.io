# Richard Orellana — portfolio

Static bilingual portfolio published at [itsmerichart.github.io](https://itsmerichart.github.io/).

## Structure

- `index.html` — page structure and default English copy.
- `styles.css` — responsive styling.
- `app.js` — English/Spanish translations and the repository archive.
- `assets/Richard_Orellana_CV.pdf` — downloadable CV.
- `data/public-repositories.json` — snapshot of public GitHub repositories.

The page is intentionally buildless. GitHub Pages serves the files from the root of `main`.

## Local preview

Run `python3 -m http.server 8000` in this directory, then open `http://localhost:8000/` in a browser. Use `?lang=es` to preview Spanish directly.

## Content updates

The Kurius Chocolate companion iOS app is mentioned without a store link while it is under App Store review. When the listing is public, update the Kurius project links in `index.html` and the corresponding translations in `app.js`.

To refresh the public repository snapshot while authenticated to GitHub CLI as `ItsMeRichArt`:

```sh
gh api 'users/ItsMeRichArt/repos?per_page=100&type=owner&sort=updated' \
  --jq '[.[] | {name,description,html_url,homepage,language,archived,fork,updated_at}]' \
  > data/public-repositories.json
```

The site shows the public repository archive, excluding forks, the GitHub profile repository, and this portfolio repository. Client source stays private.

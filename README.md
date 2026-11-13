# rheysoft.github.io

Source of the website rheysoft.com: the landing page, the Impressum, the general privacy policy (German and English) and the privacy policies of individual products.

## Public repository, live branch

This repository is public, including its complete history. The branch `main` is published by GitHub Pages to rheysoft.com. Every push to `main` goes live immediately, so changes are prepared on separate branches and merged into `main` only when they are ready to be published.

## Preview locally

The pages are static HTML with root-relative paths (for example `/fonts.css`), so serve them from the repository root:

```bash
python -m http.server 8000
```

Then open http://localhost:8000/. Extensionless links such as `/datenschutz` or `/privacy` only resolve on GitHub Pages; locally, open the `.html` file instead.

## Publishing

Pushing to `main` triggers the GitHub Pages build and publishes the site at rheysoft.com. `_config.yml` keeps repository files such as this README and the LICENSE out of the published site.

## Owner and licence

The content belongs to rheysoft UG (haftungsbeschränkt). It is proprietary; see [LICENSE](LICENSE).

## Contact

rheysoft@gmail.com

# Yihang Zhu — personal site

Built with [MkDocs](https://www.mkdocs.org/) and the
[Material](https://squidfunk.github.io/mkdocs-material/) theme. Content lives in
`docs/` as plain Markdown; appearance is controlled by `mkdocs.yml` and
`docs/stylesheets/extra.css`.

## Preview locally

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve
```

Then open <http://127.0.0.1:8000>. The page reloads as you save files.

## Deploy to GitHub Pages

```bash
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/YihangZhu/yihang-site.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Build and deployment → Source → GitHub
Actions**. The workflow in `.github/workflows/deploy.yml` runs on every push to
`main` and publishes the built site.

## Adding a page

1. Create the `.md` file under `docs/`.
2. Add it to the `nav:` tree in `mkdocs.yml`.
3. Commit and push.

Note that `mkdocs build --strict` fails on broken internal links, so a typo in a
link will stop the deploy rather than shipping a dead page.

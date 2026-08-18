# Yihang Zhu — personal site

Built with [MkDocs](https://www.mkdocs.org/) and the
[Material](https://squidfunk.github.io/mkdocs-material/) theme. Content lives in
`docs/` as plain Markdown; appearance is controlled by `mkdocs.yml` and
`docs/stylesheets/extra.css`.

## Still to do

1. **Add the remaining tutorial figures.** Two pages still carry a "Figure to
   add" callout where Google Sites had a screenshot: `train-on-colab.md` (four
   images) and `tips-for-ml-training.md` (one). Save them out of the old site
   into `docs/imgs/` and swap the callouts for image links, following the
   pattern now used in `training-with-multiple-gpus.md`.

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

## Writing pages

Fenced code blocks get syntax highlighting and a copy button:

````markdown
```bash
sbatch job.slurm
```
````

Callouts:

```markdown
!!! note
    Check the queue with `squeue -u $USER`.

!!! warning
    Requesting more GPUs than the partition has will silently queue forever.
```

Collapsible sections, tabs, footnotes and tables are also available — see the
`markdown_extensions` list in `mkdocs.yml`.

## The hidden `else/` section

`docs/else/` holds working notes. It is deliberately kept out of `nav:` in
`mkdocs.yml`, so it never appears in the menu. Reach it directly at
<https://YihangZhu.github.io/yh-site/else/>.

Each page in there carries this front matter, which keeps it out of the site
search index and tells search engines not to index it:

```yaml
---
noindex: true
search:
  exclude: true
---
```

The `noindex` flag is handled by `overrides/main.html` (emits the robots meta
tag) and `overrides/sitemap.xml` (leaves the page out of `sitemap.xml`).

**This is unlisted, not private.** The repository is public, so anyone with the
URL can read these pages and the Markdown source is visible on GitHub. For
anything genuinely private, keep it out of this repo.

## Adding a page

1. Create the `.md` file under `docs/`.
2. Add it to the `nav:` tree in `mkdocs.yml`.
3. Commit and push.

Note that `mkdocs build --strict` fails on broken internal links, so a typo in a
link will stop the deploy rather than shipping a dead page.

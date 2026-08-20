---
noindex: true
search:
  exclude: true
---

# Else

Working notes. Not linked from the site menu, excluded from site search, and
marked `noindex` so search engines skip it.

!!! warning "This is unlisted, not private"
    The repository is public, so these pages are readable by anyone who knows
    the URL, and the Markdown source is visible on GitHub. Keep anything you'd
    mind a stranger reading out of here.

## Technical

- [Machine Learning Notes](MLnotes.md)
- [Python-related](Pythonrelated.md)
- [Linux-related](Linuxrelated.md)
- [Yihang's website — LaTeX](LaTeX.md)
- [Miscellany](Miscellany.md)

## Travel

- [Travel - UK](TravelUK.md)
- [Travel - Morocco](Travelmorocco.md)

## Adding another page

1. Create the `.md` file in `docs/else/`.
2. Give it this front matter, exactly:

    ```yaml
    ---
    noindex: true
    search:
      exclude: true
    ---
    ```

3. Add a link to it in a list above. Do **not** add it to `nav:` in
   `mkdocs.yml` — that is what keeps it out of the menu.

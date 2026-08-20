---
noindex: true
search:
  exclude: true
---

## Documents

- **Sublime-text editor**: download [here](https://www.sublimetext.com/download)
- **LatexTools for Sublime**: [installation and setup in different systems](https://latextools.readthedocs.io/en/latest/install/)
- **Wiki book for LaTeX** is available [here](https://en.wikibooks.org/wiki/LaTeX). The commonly used, e.g., [mathematics](https://en.wikibooks.org/wiki/LaTeX/Mathematics), [Advanced Mathematics](https://en.wikibooks.org/wiki/LaTeX/Advanced_Mathematics), Glossary ([Abbreviations manager](https://en.wikibooks.org/wiki/LaTeX/Glossary))
- **Setup PyCharm for LaTeX**: <https://github.com/Hannah-Sten/TeXiFy-IDEA/wiki/Installation#mac-instructions>

## Tips

- **Bold style for math symbols**: `\usepackage{bm}` + `\boldsymbol{}` (details are [here](https://tex.stackexchange.com/questions/595/how-can-i-get-bold-math-symbols))
- **New line in a table cell**: `\usepackage{makecell}` `\makecell{a\\b}`
- **Subfigure**:

```latex
\begin{figure}[!htp]
\centering
%require \usepackage{subfigure}
\subfigure[subcaption1 \label{fig:0}]{
  \resizebox{0.45\linewidth}{!}{
  % require \usepackage{graphicx}
  % trim={left bottom right top}
  \includegraphics[clip, trim=0cm 5cm 0cm 4cm, scale=1]{fig/fig1.pdf}}
}\hfill
\subfigure[subcaption 2 \label{fig:1}]{
  \resizebox{0.45\linewidth}{!}{
  \includegraphics[clip, trim=0cm 5cm 0cm 4cm, scale=1]{fig/fig2.pdf}}}
\caption{aabababa}
\label{fig:bbb}
\end{figure}
```

- **Deeply nested list** via, e.g., `enumerate` or `itemize`: [solution](https://stackoverflow.com/questions/1935952/maximum-nesting-level-of-lists-in-latex)
- **Fancy colours**: `\usepackage[dvipsnames]{xcolor}`. More details are available [here](https://en.wikibooks.org/wiki/LaTeX/Colors).
- **`\argmax`**: <https://tex.stackexchange.com/questions/5223/command-for-argmin-or-argmax>
- **Compile problem of `nomencl`**: <https://tex.stackexchange.com/questions/27824/using-package-nomencl>
- **`printglossary` issue on Mac**: <https://tex.stackexchange.com/questions/43759/printglossaries-is-not-generating-anything-for-me>
- **Customize item label**: <https://mirror.koddos.net/CTAN/macros/latex/contrib/enumitem/enumitem.pdf>
- **Item spacing**: <https://stackoverflow.com/questions/1061112/eliminate-space-before-beginitemize>
- **Draw lines in equation**: <https://tex.stackexchange.com/questions/265787/connecting-parts-of-equations-with-lines>
- **Set depth for sections**: <https://tex.stackexchange.com/questions/130795/how-can-i-number-sections-below-subsection-in-latex>
- **LaTeX colour**: <https://latexcolor.com/>
- **`makecell` package**: <https://mirrors.ibiblio.org/CTAN/macros/latex/contrib/makecell/makecell.pdf>
- **Using LaTeX in Python plot title**: <https://stackoverflow.com/questions/46698921/latex-and-text-in-matplotlib-title>
- **Theorem-related environments** are introduced [here](https://www.overleaf.com/learn/latex/Theorems_and_proofs).

## Tools

- **Optimizing bib file**: [Online bibtex tidy](https://flamingtempura.github.io/bibtex-tidy/index.html?opt=%7B%22curly%22%3Atrue%2C%22numeric%22%3Atrue%2C%22space%22%3A2%2C%22tab%22%3Atrue%2C%22align%22%3A13%2C%22duplicates%22%3A%5B%22key%22%5D%2C%22stripEnclosingBraces%22%3Afalse%2C%22dropAllCaps%22%3Afalse%2C%22escape%22%3Afalse%2C%22sortFields%22%3A%5B%22title%22%2C%22shorttitle%22%2C%22author%22%2C%22year%22%2C%22month%22%2C%22day%22%2C%22journal%22%2C%22booktitle%22%2C%22location%22%2C%22on%22%2C%22publisher%22%2C%22address%22%2C%22series%22%2C%22volume%22%2C%22number%22%2C%22pages%22%2C%22doi%22%2C%22isbn%22%2C%22issn%22%2C%22url%22%2C%22urldate%22%2C%22copyright%22%2C%22category%22%2C%22note%22%2C%22metadata%22%5D%2C%22stripComments%22%3Afalse%2C%22trailingCommas%22%3Afalse%2C%22encodeUrls%22%3Afalse%2C%22tidyComments%22%3Atrue%2C%22removeEmptyFields%22%3Afalse%2C%22removeDuplicateFields%22%3Afalse%2C%22lowercase%22%3Atrue%2C%22backup%22%3Atrue%7D)
- **Google table to LaTeX**: [spread-latex](https://workspace.google.com/marketplace/app/spreadlatex/218144906748)
- **Units**: `\usepackage{siunitx}` e.g., `\SI{100}{\meter}`

[Back to Else](index.md)

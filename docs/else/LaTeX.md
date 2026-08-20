---
noindex: true
search:
  exclude: true
---

# Yihang's website — LaTeX

## Documents

- **Sublime-text editor**: download here
- **LatexTools for Sublime**: installation and setup in different systems
- **Wiki book for LaTeX** is available here. The commonly used, e.g., mathematics, Advanced Mathematics, Glossary (Abbreviations manager)
- **Setup PyCharm for LaTeX**: <https://github.com/Hannah-Sten/TeXiFy-IDEA/wiki/Installation#mac-instructions>

## Tips

- **Bold style for math symbols**: `\usepackage{bm}` + `\boldsymbol{}` (details are here)
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

- **Deeply nested list** via, e.g., `enumerate` or `itemize`: solution
- **Fancy colours**: `\usepackage[dvipsnames]{xcolor}`. More details are available here.
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
- **Theorem-related environments** are introduced here.

## Tools

- **Optimizing bib file**: Online bibtex tidy
- **Google table to LaTeX**: spread-latex
- **Units**: `\usepackage{siunitx}` e.g., `\SI{100}{\meter}`

[Back to Else](index.md)

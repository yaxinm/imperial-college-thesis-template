# Thesis Template

This template meets the college guidelines for 2025.
Please see instructions in **main.pdf**.

## How to compile

### Overleaf

Upload all files into an Overleaf project, then press **compile**.

### Locally
You will need to install latex locally, please follow the instruction on the [LaTeX website](https://www.latex-project.org/get/).
If you are using "main.tex" as your main document (which is the default of this repo), run the following command.
```
pdflatex main
bibtex main
pdflatex main
pdflatex main
```
It will give a warning if you haven't cited anything yet.


## Specific instructions for documents with Nomenclature
The command `makeindex` is necessary to output the nomenclature. You may need to install the package *nomencl* first.

### Overleaf

Run **compile** on Overleaf.

### Local installation

To get the Nomenclature, build using the following commands, assuming you are using "main.tex" as your main document.
```
pdflatex main
bibtex main
makeindex main.nlo -s nomencl.ist -o main.nls
pdflatex main
pdflatex main
```

#### VSCode

If you are using **VSCode** with the extension **latex-workshop** to compile, you may need to define a new recipe.
Add the following to LaTeX `latex-workshop.latex.tools`.
```
{
    "name": "makenomenclature",
    "command": "makeindex",
    "args": [
        "%DOCFILE%.nlo",
        "-s",
        "nomencl.ist",
        "-o",
        "%DOCFILE%.nls"
    ]
},
```
And the following under `latex-workshop.latex.recipes`.
```
{
    "name": "pdflatex,bibtex,nomenclature",
    "tools": [
        "pdflatex",
        "bibtex",
        "makenomenclature",
        "pdflatex",
        "pdflatex"
    ]
},
```

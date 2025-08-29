# Thesis Template

Please see instructions in **main.pdf**.

## How to compile

Upload all files into an Overleaf project, or download 
Press **compile** on Overleaf, or you will need the following command to compile.


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

Install the extension **latex-workshop**.
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

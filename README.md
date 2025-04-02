# Accessible Thesis Template

This thesis template is meant to provide the basis for creating an accessible
thesis.

It utilizes the [latex tagging project instructions](https://latex3.github.io/tagging-project/documentation/prototype-usage-instructions.html)

Attempting to modify the old university templates to use `\DocumentMetadata`
were not successful. Instead, I opted to use the standard book class in order
to maintain compatibility with the ongoing tagging effort.

Instructions for the university's accessibility requirements can be found under
[Digital Accessibility
Requirements](https://case.edu/gradstudies/current-students/electronic-theses-and-dissertation-guidelines).
Please also see
[instructions](https://case.edu/gradstudies/sites/default/files/2024-06/Digital%20Accessibility%20Guide%20for%20Adobe%20Acrobat%20Pro.pdf)
for using Acrobat to generate an accessibility report.

## Quick Start Guide

In general, search for `TODO` in `thesis.tex` and edit where appropriate.

You need to edit the section in `thesis.tex` where hypersetup sets several pdf
metadata fields as shown below.

```latex
%TODO Change these
\hypersetup{
    pdflang={en},
    pdftitle={the title},
    pdfauthor={the author},
    pdfsubject={what subject},
    pdfkeywords={comma delimited keywords},
    hidelinks
}
```

Add your content to the files in the `/contents` folder.

Add `alt` tags to figures as described
[here](https://latex3.github.io/tagging-project/documentation/prototype-usage-instructions#handling-graphics-in-the-document)
and shown below

```latex
\begin{figure}[hbt!]
    \centering
    \includegraphics[width=.5\textwidth,alt={This is alt text for a figure of the CWRU logo.}]{cwru_logo.eps}
    \caption{This is a figure of the CWRU logo.}
    \label{fig:logo}
\end{figure}
```

TODO: what else is needed for accessible pdfs?

## Prerequisites

You will want a recent tex installation like
[tex-live](https://www.tug.org/texlive/) 2025.

You want [`make`](https://www.gnu.org/software/make/). You can install make in
Ubuntu Linux by running `apt install build-essential`. Alternatively, use
something like VS Code and the LaTeX Workshop plugin.

## Building

In this folder, run `make`

Look for the file `thesis.pdf`

Cleaning `make clean`

## Useful Tips

Code editors are generally lacking in finding typos and mistakes. You can export
to a word format using pandoc to facilitate spelling and grammar checking.

```sh
pandoc thesis.tex -s -o thesis-2025-03-11-0100.docx
```

If using VS Code, the rewrap plugin is really useful to
manage text lines so they don't get too long.

I used this website to submit sample thesis to see what issues existed.
https://pave-pdf.org/index.html?lang=en


### Memory issue when building

Issue with inability to compile,  The following was found in the `thesis.log` file:

```
TeX capacity exceeded, sorry [main memory size=5000000].
```

Had to modify `/some/path/to/texlive/some/subpath/web2c/texmf.cnf` for the `main_memory = 5000000` line to `main_memory = 10000000`

and then run:

```
sudo fmtutil-sys --all
```

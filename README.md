# Accessible Thesis

This thesis template is meant to provide the basis for creating an accessible thesis.

It utilizes the [latex tagging project instructions](https://latex3.github.io/tagging-project/documentation/prototype-usage-instructions.html)

You should edit the section in `thesis.tex` where hypersetup sets several pdf metadata fields.

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

It looks like you need to add `alt` tags to figures as described
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

You want `make`(https://www.gnu.org/software/make/). You can install make in
Ubuntu Linux by running `apt install build-essential`. Alternatively, use
something like VS Code and the LaTeX Workshop plugin.

## Building

In this folder, run `make`

Look for the file `thesis.pdf`

Cleaning `make clean`

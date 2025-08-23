+++
publish = false
+++

# Diagrams for _Quantum Field Theory_

This folder contains the source code for all the Feynman diagrams in the QFT book. The Feynman diagrams are drawn with LaTeX using the `feynmp-auto` package, and then converted to SVGs for inclusion in the book.

## Development

To convert the LaTeX output to SVGs, the following semi-automated process is used:

1. Using a LaTeX compiler (or [Overleaf](https://overleaf.com)) compile the LaTeX sources into a PDF
2. Use [Inkscape](https://inkscape.org) to convert the PDF to an SVG. This can be done on the command-line with `inkscape THE_DIAGRAM.pdf -o THE_SVG.svg`
3. Manually resize the diagram in Inkscape by resizing the document to a width of 400px and height of 300px, and centering-aligning the whole diagram

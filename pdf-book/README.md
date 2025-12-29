# PDF version of theoretical physics book

This directory will eventually house ready-to-download PDF versions of the [learner's guide to theoretical physics](https://learntheoreticalphysics.com/). The plan is to have several individual volumes corresponding to each of the separate books (quantum field theory, relativity, etc.) as well as a combined version with all the volumes in one book.

Currently, there is no build step to create the books from the sources (in the `content/` folder in the root of the repo), which will likely require using [pandoc](https://pandoc.org/) to build the books by converting them from markdown to LaTeX. There is an experimental test LaTeX version available in [main.tex](./main.tex), with a [PDF preview available](outputs/book.pdf).

#SHELL := /bin/bash

build: paper.pdf

show : paper.pdf
	okular $<

paper.pdf: paper.tex figure/topology-conference.pdf figure/steak-rendering.pdf
	pdflatex $< && \
	bibtex paper && \
	pdflatex $< && \
	pdflatex $< || rm $@

%.tex : %.Rnw
	Rscript -e "library(knitr); knit('$<')" || (rm $@ && exit -1)

%.pdf : %.svg
	inkscape $< --export-pdf=$@

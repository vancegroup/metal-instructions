
tuftefiles := hardwrap.sty tufte-book.cls tufte-book.layout tufte.bst tufte-common.def tufte-handout.cls tufte-handout.layout

all: Manual.pdf

%.pdf: %.lyx $(tuftefiles)
	-rm $@
	lyx -e pdf2 $<

.PHONY: all

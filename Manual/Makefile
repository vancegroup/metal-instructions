tuftefiles := hardwrap.sty tufte-book.cls tufte-book.layout tufte.bst tufte-common.def tufte-handout.cls tufte-handout.layout
otherinputs := ../quickstart/windows.pdf
OUTPUTS := Manual.pdf

all: $(OUTPUTS)

clean:
	rm -f $(OUTPUTS)

%.pdf: %.lyx $(tuftefiles)
	-rm $@
	lyx -e pdf2 $<

.PHONY: all clean

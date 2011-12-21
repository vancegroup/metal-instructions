#! make

# Makefile to generate rendered versions of SVG logos
# requires gnu make and a reasonably recent inkscape

# Directories
inputdir := svg-originals
vectordir := vector-scalable-exports
bitmapdir := png-bitmap-exports

# Name parts
transparentname := transparent
whitename := whitebg
smallname := small
mediumname := medium
largename := large

# inkscape commands
INKSCAPE=@echo "\n[EXPORTING] $@" && inkscape --without-gui --file=$<
VECTORFLAGS=--export-text-to-path

# Base names of all input svg files
inputs := $(patsubst $(inputdir)/%.svg,%,$(wildcard $(inputdir)/*.svg))

# 
epsfiles := $(patsubst %,$(vectordir)/%.eps,$(inputs))
pdffiles := $(patsubst %,$(vectordir)/%.pdf,$(inputs))

pngwhitesmallfiles := $(patsubst %,$(bitmapdir)/%_$(whitename)_$(smallname).png,$(inputs))
pngwhitemediumfiles := $(patsubst %,$(bitmapdir)/%_$(whitename)_$(mediumname).png,$(inputs))
pngwhitelargefiles := $(patsubst %,$(bitmapdir)/%_$(whitename)_$(largename).png,$(inputs))
pngwhitefiles := $(pngwhitesmallfiles) $(pngwhitemediumfiles) $(pngwhitelargefiles)

pngtranssmallfiles := $(patsubst %,$(bitmapdir)/%_$(transparentname)_$(smallname).png,$(inputs))
pngtransmediumfiles := $(patsubst %,$(bitmapdir)/%_$(transparentname)_$(mediumname).png,$(inputs))
pngtranslargefiles := $(patsubst %,$(bitmapdir)/%_$(transparentname)_$(largename).png,$(inputs))
pngtransfiles := $(pngtranssmallfiles) $(pngtransmediumfiles) $(pngtranslargefiles)

outputs := $(epsfiles) $(pdffiles) $(pngwhitefiles) $(pngtransfiles)
whitebgflag := --export-background-opacity=100
transbgflag := --export-background-opacity=0
smallflag := --export-dpi=30
mediumflag := --export-dpi=90
largeflag := --export-dpi=120

all: vector bitmap

vector: eps pdf

eps: $(epsfiles)
pdf: $(pdffiles)

bitmap: pngwhite pngtrans

pngwhite: $(pngwhitefiles)

pngtrans: $(pngtransfiles)

outputs: $(MAKEFILE)

clean:
	-rm $(outputs)
	#-rmdir $(vectordir)
	#-rmdir $(bitmapdir)

$(vectordir) $(bitmapdir):
	@echo Creating directory $@
	@mkdir -p $@

$(epsfiles): $(vectordir)/%.eps: $(inputdir)/%.svg $(vectordir) $(MAKEFILE)
	$(INKSCAPE) --export-eps=$@ $(VECTORFLAGS)

$(pdffiles): $(vectordir)/%.pdf: $(inputdir)/%.svg $(vectordir) $(MAKEFILE)
	$(INKSCAPE) --export-pdf=$@ $(VECTORFLAGS)

$(pngwhitesmallfiles): $(bitmapdir)/%_$(whitename)_$(smallname).png: $(inputdir)/%.svg $(bitmapdir) $(MAKEFILE)
	$(INKSCAPE) --export-png=$@ $(whitebgflag) $(smallflag)

$(pngwhitemediumfiles): $(bitmapdir)/%_$(whitename)_$(mediumname).png: $(inputdir)/%.svg $(bitmapdir) $(MAKEFILE)
	$(INKSCAPE) --export-png=$@ $(whitebgflag) $(mediumflag)

$(pngwhitelargefiles): $(bitmapdir)/%_$(whitename)_$(largename).png: $(inputdir)/%.svg $(bitmapdir) $(MAKEFILE)
	$(INKSCAPE) --export-png=$@ $(whitebgflag) $(largeflag)

$(pngtranssmallfiles): $(bitmapdir)/%_$(transparentname)_$(smallname).png: $(inputdir)/%.svg $(bitmapdir) $(MAKEFILE)
	$(INKSCAPE) --export-png=$@ $(transbgflag) $(smallflag)

$(pngtransmediumfiles): $(bitmapdir)/%_$(transparentname)_$(mediumname).png : $(inputdir)/%.svg $(bitmapdir) $(MAKEFILE)
	$(INKSCAPE) --export-png=$@ $(transbgflag) $(mediumflag)

$(pngtranslargefiles): $(bitmapdir)/%_$(transparentname)_$(largename).png : $(inputdir)/%.svg $(bitmapdir) $(MAKEFILE)
	$(INKSCAPE) --export-png=$@ $(transbgflag) $(largeflag)


.PHONY: all vector eps pdf bitmap pngwhite pngtrans clean

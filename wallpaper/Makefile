#! make

pngfiles = headnode.png rendernode.png rendernode-login.png
bmpfiles = $(pngfiles:.png=.bmp)
outputs = $(pngfiles) $(bmpfiles)

inputdir := sources

all: png bmp

png: $(pngfiles)
bmp: $(bmpfiles)

clean:
	-rm $(outputs)

headnode.png rendernode-login.png: %.png: $(inputdir)/%.svg
	inkscape --without-gui --file=$< --export-png=$@

rendernode-login.png: $(inputdir)/fyre-cyclone.png
headnode.png: $(inputdir)/cyclone-19201200.png $(inputdir)/alternate-vrac/VRAC_HCI_logo_white_sm.png

rendernode.png: $(inputdir)/fyre-cyclone.png
	cp $< $@

$(bmpfiles): %.bmp: %.png $(MAKEFILE)
	convert -depth 24 $< -alpha opaque bmp3:$@


.PHONY: all png bmp clean

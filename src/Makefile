PKG =  RollingStats

$(PKG).gfn: $(PKG).inp $(PKG).spec $(PKG)_help.txt $(PKG)_sample.inp
	gretlcli --makepkg $(PKG).inp

#$(PKG).pdf: $(PKG).tex
#	pdflatex $<
#	bibtex $(PKG)
#	pdflatex $<
#	pdflatex $<

#$(PKG).zip: $(PKG).gfn $(PKG).pdf
#	echo makepkg $(PKG).zip | gretlcli -b -

# Only if the manual is a pdf file or you provide an external dataset
#install: $(PKG).zip
#	echo pkg install $(PKG).zip --local | gretlcli -b -

install: $(PKG).gfn
	echo pkg install $(PKG).gfn --local | gretlcli -b -

# Only for zip-file
#clean:
#	rm -f $(PKG).zip

#clean:
#	rm -f $(PKG).gfn

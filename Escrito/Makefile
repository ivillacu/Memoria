# Makefile
TEXFILES = $(wildcard *.tex)
PDFFILES = $(TEXFILES:.tex=.pdf)

all: pdflatex clean

pdf: $(PDFFILES)

pdflatex: $(TEXFILES)
	$(foreach x,$(TEXFILES:.tex=),pdflatex $(x);)
	#$(foreach x,$(TEXFILES:.tex=),bibtex $(x);)
	#$(foreach x,$(TEXFILES:.tex=),pdflatex $(x);)
	$(foreach x,$(TEXFILES:.tex=),pdflatex $(x);)
	@if [ -d publish ];then mv *.pdf publish; else mkdir publish; mv *.pdf publish/;fi

clean:
	@rm -f *.bbl *.blg
	@rubber --clean $(TEXFILES:.tex=)

distclean: clean
	@rubber --clean --pdf $(TEXFILES:.tex=)
	@rm -rf publish
	@rm -f $(PDFFILES)

x:
	@open publish/$(PDFFILES) &> /dev/null &

export TEXINPUTS:=.:formatting:$(TEXINPUTS)

CROSSTEX := crosstex
CROSSTEX_ARGS := --titlecase lower --add-in --short=author --short=conference

BIBTEX   := bibtex

FIGFIGS :=
EPSFIGS := 
PNGFIGS :=
PDFFIGS :=
SVGFIGS := 
GNUPLOTFIGS :=
FIGS    := $(FIGFIGS) $(EPSFIGS) $(PDFFIGS) $(SVGFIGS) $(GNUPLOTFIGS) \
           $(PNGFIGS)

TEX_SOURCES := paper.tex 

.SUFFIXES:

all: 
	pdflatex paper
	bibtex paper
	pdflatex paper
	pdflatex paper

pdf: paper.pdf

commit: 
	git commit -m "Added stuff" -a
	git push origin master


spell: $(TEX_SOURCES)
	detex $^ | spell | env LANG=C sort -u | env LANG=C comm -23 - ok-words

clean:
	rm -f *~ *.log *.bbl *.dvi paper.pdf *.blg *.aux *.ps *.out

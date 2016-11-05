GSCMD = rungs

base = snowman0-kozuka snowman0-hiragino snowman0-yuosx \
	snowman0-sourcehansans snowman0-ipa snowman0-meiryo

kozuka = KozMinPr6N-Regular
hiragino = HiraMinProN-W3
yuosx = YuMincho-Demibold
sourcehansans = SourceHanSans-Regular
ipa = IPAexMincho
meiryo = Meiryo

all: $(addsuffix .pdf,$(base))

.SUFFIXES: .tex .pdf

%.tex:
	cp snowman-img.tex $@

.tex.pdf:
	echo $($(patsubst %.tex,%,$(patsubst snowman0-%,%,$<))) | xelatex $<
	$(GSCMD) -dBATCH -dNOPAUSE -dNoOutputFonts -q -sDEVICE=pdfwrite -sOutputFile=$@-outline.pdf $@
	mv $@-outline.pdf $@
	rm *.aux *.log

.PHONY: clean
clean:
	rm -f *.pdf

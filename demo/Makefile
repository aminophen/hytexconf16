KANJI = -kanji=utf8
FONTMAP = -f hiraginopron.map -f ptex-hiragino-pron.map

base = demo01-DATE.pdf demo02-DATE.pdf demo03-DATE.pdf \
	demo04-DATE.pdf demo05-DATE.pdf demo06-DATE.pdf \
	demo07-DATE.pdf
basex = exp01-DATE.pdf exp02-DATE.pdf

old = $(subst DATE,2012,$(base))
medium = $(subst DATE,2013,$(base))
new = $(subst DATE,2016,$(base))
current = $(subst DATE,2016,$(basex))
exp = $(subst DATE,2017,$(basex))

all: $(old) $(medium) $(new) $(current) $(exp)

.SUFFIXES: .tex .dvi .pdf

%-2012.tex:
	cp $(patsubst %-2012.tex,%.tex,$@) $@
	echo "\RequirePackage[2012/10/01]{platexrelease-demo}" >platex.cfg
%-2013.tex:
	cp $(patsubst %-2013.tex,%.tex,$@) $@
	echo "\RequirePackage[2013/10/01]{platexrelease-demo}" >platex.cfg
%-2016.tex:
	cp $(patsubst %-2016.tex,%.tex,$@) $@
	echo "\RequirePackage[2016/09/08]{platexrelease-demo}" >platex.cfg
%-2017.tex:
	cp $(patsubst %-2017.tex,%.tex,$@) $@
	echo "\RequirePackage{exppl2e}" >platex.cfg

.tex.dvi:
	platex $(KANJI) $<
	platex $(KANJI) $<
	rm *.aux *.log platex.cfg
.dvi.pdf:
	dvipdfmx $(FONTMAP) $<

.PHONY: clean
clean:
	rm -f *.dvi *.pdf platex.cfg

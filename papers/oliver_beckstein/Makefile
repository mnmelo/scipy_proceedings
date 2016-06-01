# quick and dirty paper generation (remove before final PR)

NAME := oliver_beckstein
PAPERDIR := papers/$(NAME)
OUTPUTDIR := output/$(NAME)

RST  := $(NAME).rst
BIB  := mdanalysis.bib
BUILDPDF  := paper.pdf
PDF  := MDAnalysis_SciPy_2016.pdf

TOPDIR  := $(shell git rev-parse --show-toplevel)

.phony: all pdf see rebase

all: pdf

pdf: $(PDF)

$(PDF): $(RST) $(BIB)
	-rm -r "$(TOPDIR)/$(OUTPUTDIR)"
	cd $(TOPDIR) && \
	./make_paper.sh $(PAPERDIR) && \
        ./make_paper.sh $(PAPERDIR) && \
	cp -v $(OUTPUTDIR)/$(BUILDPDF) $(PAPERDIR)/$(PDF)

see: $(PDF)
	open $^

rebase:
	git rebase 2016
	-rm $(PDF)
	$(MAKE) $(PDF) && git add $(PDF)


THISDIR := phy487-qmsolids
THISBOOK := phy487

BIBLIOGRAPHY_PATH := classicthesis_mine
HAVE_OWN_CONTENTS := 1
MY_CLASSICTHESIS_FRONTBACK_FILES += ../latex/classicthesis_mine/FrontBackmatter/Index.tex
MY_CLASSICTHESIS_FRONTBACK_FILES += ../latex/classicthesis_mine/FrontBackmatter/ContentsAndFigures.tex
BOOKTEMPLATE := ../latex/classicthesis_mine/ClassicThesis2.tex

include make.revision
include ../latex/make.bookvars

#ONCEFLAGS := -justonce

# uncomment-in for kdp version (no mathematica notebooks in appendix.)
#PRINT_VERSION := 1
ifdef PRINT_VERSION
DISTEXTRA := kdp
else
PARAMS += --no-print
endif

SOURCE_DIRS += appendix
# FIXME:
# 1) including this incorrectly adds figures/*pdf to the ./.gitignore file
# 2) also not seeing this result in figure dependencies. touch figures/etalonFig1.pdf
FIGURES := ../figures/phy487-qmsolids

SOURCE_DIRS += $(FIGURES)

GENERATED_SOURCES += mathematica.tex 
GENERATED_SOURCES += backmatter.tex

EPS_FILES := $(wildcard $(FIGURES)/*.eps)
PDFS_FROM_EPS := $(subst eps,pdf,$(EPS_FILES))

THISBOOK_DEPS += $(PDFS_FROM_EPS)

DO_SPELL_CHECK := $(shell cat spellcheckem.txt)

include ../latex/make.rules

.PHONY: spellcheck
spellcheck: $(patsubst %.tex,%.sp,$(filter-out $(DONT_SPELL_CHECK),$(DO_SPELL_CHECK)))

%.sp : %.tex
	spellcheck $^
	touch $@

condensedMatterProblemSet1.pdf :: condensedMatterProblemSet1Problem1.tex
condensedMatterProblemSet1.pdf :: condensedMatterProblemSet1Problem2.tex
condensedMatterProblemSet1.pdf :: condensedMatterProblemSet1Problem3.tex

condensedMatterProblemSet1.pdf :: $(PDF_DEPS)

condensedMatterProblemSet2.pdf :: condensedMatterProblemSet2Problem1.tex
condensedMatterProblemSet2.pdf :: condensedMatterProblemSet2Problem2.tex
condensedMatterProblemSet2.pdf :: condensedMatterProblemSet2Problem3.tex

condensedMatterProblemSet2.pdf :: $(PDF_DEPS)

condensedMatterProblemSet5.pdf :: condensedMatterProblemSet5Problem1.tex
condensedMatterProblemSet5.pdf :: condensedMatterProblemSet5Problem2.tex
condensedMatterProblemSet5.pdf :: condensedMatterProblemSet5Problem3.tex

condensedMatterProblemSet5.pdf :: $(PDF_DEPS)

condensedMatterLecture7PhononsQ.pdf :: $(PDF_DEPS)
condensedMatterLecture7PhononsQ.pdf :: condensedMatterLecture7Phonons.tex

condensedMatterLecture6q.pdf :: $(PDF_DEPS)
condensedMatterLecture6q.pdf :: condensedMatterLecture6.tex

backmatter.tex: ../latex/classicthesis_mine/backmatter2.tex
	rm -f $@
	ln -s ../latex/classicthesis_mine/backmatter2.tex backmatter.tex

THISDIR := phy487-qmsolids
THISBOOK := phy487

export BOOKSUBVER := 1
export BOOKMAJVER := 0
export REVISIONNUMBER := 8

#.revinfo/gitCommitDateAsMyTime.tex:\newcommand{\myTime}{April 2018}\newcommand{\myVersion}{version V0.117\xspace}
VER := $(shell grep Version .revinfo/gitCommitDateAsMyTime.tex | sed 's/.*{//;s/.xspace.*//;')

include ../latex/make.bookvars

#ONCEFLAGS := -justonce

SOURCE_DIRS += appendix
# FIXME:
# 1) including this incorrectly adds figures/*pdf to the ./.gitignore file
# 2) also not seeing this result in figure dependencies. touch figures/etalonFig1.pdf
FIGURES := ../figures/phy487-qmsolids

SOURCE_DIRS += $(FIGURES)

# also toggle redacted classicthesis-config.tex
# FIXME: changing this flag should be a dependency of mathematica.tex 
#REDACTED := -redacted

GENERATED_SOURCES += mathematica.tex 

EPS_FILES := $(wildcard $(FIGURES)/*.eps)
PDFS_FROM_EPS := $(subst eps,pdf,$(EPS_FILES))

THISBOOK_DEPS += $(PDFS_FROM_EPS)

include ../latex/make.rules

dist:
	cp $(THISBOOK).pdf $(THISBOOK).$(VER).pdf

# a for annotate (releases).
tag:
	git tag -a $(THISBOOK).$(VER).pdf

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

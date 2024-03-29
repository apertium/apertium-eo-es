LANG1=eo
LANG2=es
PREFIX1=$(LANG2)-$(LANG1)
PREFIX2=$(LANG2)-$(LANG1)-no_cg

BASENAME=apertium-eo-es
BILNAME=apertium-eo-es.eo-es.dix

TARGETS_COMMON = $(PREFIX1).automorf.bin $(PREFIX1).autobil.bin $(PREFIX1).autogen.bin $(PREFIX1).autopgen.bin \
     $(PREFIX1).t1x.bin $(PREFIX1).antaux1_t2x.bin $(PREFIX1).antaux2_t2x.bin $(PREFIX1).antaux3_t2x.bin $(PREFIX1).antaux4_t2x.bin $(PREFIX1).antaux5_t2x.bin $(PREFIX1).t2x.bin $(PREFIX1).t3x.bin \
     $(PREFIX1).rlx.bin \
     modes $(PREFIX1).mode $(PREFIX2).mode

TARGETS = $(TARGETS_COMMON)

@ap_include@

$(PREFIX1).antaux1_t2x.bin: $(BASENAME).$(PREFIX1).antaux1_t2x
	apertium-validate-interchunk $(BASENAME).$(PREFIX1).antaux1_t2x
	apertium-preprocess-transfer $(BASENAME).$(PREFIX1).antaux1_t2x $@

$(PREFIX1).antaux2_t2x.bin: $(BASENAME).$(PREFIX1).antaux2_t2x
	apertium-validate-interchunk $(BASENAME).$(PREFIX1).antaux2_t2x
	apertium-preprocess-transfer $(BASENAME).$(PREFIX1).antaux2_t2x $@

$(PREFIX1).antaux3_t2x.bin: $(BASENAME).$(PREFIX1).antaux3_t2x
	apertium-validate-interchunk $(BASENAME).$(PREFIX1).antaux3_t2x
	apertium-preprocess-transfer $(BASENAME).$(PREFIX1).antaux3_t2x $@

$(PREFIX1).antaux4_t2x.bin: $(BASENAME).$(PREFIX1).antaux4_t2x
	apertium-validate-interchunk $(BASENAME).$(PREFIX1).antaux4_t2x
	apertium-preprocess-transfer $(BASENAME).$(PREFIX1).antaux4_t2x $@

$(PREFIX1).automorf.bin: $(BASENAME).$(LANG2).dix
	apertium-validate-dictionary $(BASENAME).$(LANG2).dix
	lt-comp lr $(BASENAME).$(LANG2).dix $@

$(PREFIX1).autobil.bin: $(BILNAME)
	apertium-validate-dictionary $(BILNAME)
	lt-comp rl $(BILNAME) $@

$(PREFIX1).rlx.bin: $(BASENAME).$(PREFIX1).rlx
	cg-comp $(BASENAME).$(PREFIX1).rlx  $@

$(PREFIX1).autogen.bin: $(BASENAME).$(LANG1).dix
	apertium-validate-dictionary $(BASENAME).$(LANG1).dix
	lt-comp rl $(BASENAME).$(LANG1).dix $@

$(PREFIX1).autopgen.bin: $(BASENAME).post-$(LANG1).dix
	apertium-validate-dictionary $(BASENAME).post-$(LANG1).dix
	lt-comp lr $(BASENAME).post-$(LANG1).dix $@

$(PREFIX1).t1x.bin: $(BASENAME).$(PREFIX1).t1x
	apertium-validate-transfer $(BASENAME).$(PREFIX1).t1x
	apertium-preprocess-transfer $(BASENAME).$(PREFIX1).t1x $@

$(PREFIX1).antaux5_t2x.bin: $(BASENAME).$(PREFIX1).antaux5_t2x
	apertium-validate-interchunk $(BASENAME).$(PREFIX1).antaux5_t2x
	apertium-preprocess-transfer $(BASENAME).$(PREFIX1).antaux5_t2x $@

$(PREFIX1).t2x.bin: $(BASENAME).$(PREFIX1).t2x
	apertium-validate-interchunk $(BASENAME).$(PREFIX1).t2x
	apertium-preprocess-transfer $(BASENAME).$(PREFIX1).t2x $@

$(PREFIX1).t3x.bin: $(BASENAME).$(PREFIX1).t3x
	apertium-validate-postchunk $(BASENAME).$(PREFIX1).t3x
	apertium-preprocess-transfer $(BASENAME).$(PREFIX1).t3x $@

EXTRA_DIST=$(BASENAME).$(LANG1).dix $(BILNAME) \
	   $(BASENAME).post-$(LANG1).dix \
	   $(BASENAME).$(LANG2).dix \
	   $(BASENAME).$(PREFIX1).rlx \
	   $(PREFIX1).prob \
	   $(BASENAME).$(PREFIX1).t1x \
	   $(BASENAME).$(PREFIX1).antaux1_t2x $(BASENAME).$(PREFIX1).antaux2_t2x (BASENAME).$(PREFIX1).antaux3_t2x (BASENAME).$(PREFIX1).antaux4_t2x \
	   $(BASENAME).$(PREFIX1).antaux5_t2x $(BASENAME).$(PREFIX1).t2x \
	   $(BASENAME).$(PREFIX1).t3x \
	   modes.xml

apertium_eo_es_DATA=$(PREFIX1).automorf.bin \
                    $(PREFIX1).autobil.bin \
                    $(PREFIX1).autogen.bin \
                    $(PREFIX1).autopgen.bin \
		    $(PREFIX1).rlx.bin \
		    $(PREFIX1).prob \
		    $(PREFIX1).t1x.bin \
		    $(PREFIX1).antaux1_t2x.bin $(PREFIX1).antaux2_t2x.bin $(PREFIX1).antaux3_t2x.bin $(PREFIX1).antaux4_t2x.bin \
		    $(PREFIX1).antaux5_t2x.bin $(PREFIX1).t2x.bin \
		    $(PREFIX1).t3x.bin \
		    $(BASENAME).$(PREFIX1).t1x \
		    $(BASENAME).$(PREFIX1).antaux1_t2x $(BASENAME).$(PREFIX1).antaux2_t2x $(BASENAME).$(PREFIX1).antaux3_t2x $(BASENAME).$(PREFIX1).antaux4_t2x \
		    $(BASENAME).$(PREFIX1).antaux5_t2x $(BASENAME).$(PREFIX1).t2x \
		    $(BASENAME).$(PREFIX1).t3x
#		    $(BASENAME).$(PREFIX1).t1x $(BASENAME).$(PREFIX1).antaux5_t2x $(BASENAME).$(PREFIX1).t3x

apertium_eo_esdir=$(prefix)/share/apertium/apertium-$(PREFIX1)/

noinst_DATA=modes/$(PREFIX1).mode

install-data-local: install-modes

CLEANFILES = -rf $(TARGETS) modes 

test: all
	apertium-regtest test

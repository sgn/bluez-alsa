# BlueALSA - Makefile.am
# Copyright (c) 2016-2020 Arkadiusz Bokowy

man1_MANS =
man8_MANS = bluealsa.8

if ENABLE_APLAY
man1_MANS += bluealsa-aplay.1
endif

if ENABLE_RFCOMM
man1_MANS += bluealsa-rfcomm.1
endif

SUFFIXES = .md
MOSTLYCLEANFILES = $(man1_MANS) $(man8_MANS)

.md:
	$(SED) 's/\$$VERSION\$$/@PACKAGE_STRING@/;s/\$$RELEASE_DATE\$$/@RELEASE_DATE@/' $<  | $(PANDOC) -s -f markdown -t man -o $@

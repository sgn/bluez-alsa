# BlueALSA - Makefile.am
# Copyright (c) 2016-2020 Arkadiusz Bokowy

man1_MANS =
man8_MANS = bluealsa.8
MOSTLYCLEANFILES = bluealsa.8 bluealsa.8.ronn

if ENABLE_APLAY
man1_MANS += bluealsa-aplay.1
MOSTLYCLEANFILES += bluealsa-aplay.1 bluealsa-aplay.1.ronn
endif

if ENABLE_RFCOMM
man1_MANS += bluealsa-rfcomm.1
MOSTLYCLEANFILES += bluealsa-rfcomm.1 bluealsa-rfcomm.1.ronn
endif

SUFFIXES = .md .ronn

if WITH_RONN
.ronn:
	$(RONN) --manual=BlueALSA --date=@RELEASE_DATE@ -r $<

.md.ronn:
	$(SED) '/^%/d;/^# NAME/,/^blue/{/^blue/!d;s/^/# /;b};s/^# /## /' $< >$@

else
.md:
	$(SED) 's/\$$VERSION\$$/@PACKAGE_STRING@/;s/\$$RELEASE_DATE\$$/@RELEASE_DATE@/' $<  | $(PANDOC) -s -f markdown -t man -o $@

endif

#  FLAC - Free Lossless Audio Codec
#  Copyright (C) 2001,2002,2003,2004,2005,2006,2007,2008,2009  Josh Coalson
#
#  This file is part the FLAC project.  FLAC is comprised of several
#  components distributed under difference licenses.  The codec libraries
#  are distributed under Xiph.Org's BSD-like license (see the file
#  COPYING.Xiph in this distribution).  All other programs, libraries, and
#  plugins are distributed under the GPL (see COPYING.GPL).  The documentation
#  is distributed under the Gnu FDL (see COPYING.FDL).  Each file in the
#  FLAC distribution contains at the top the terms under which it may be
#  distributed.
#
#  Since this particular file is relevant to all components of FLAC,
#  it may be distributed under the Xiph.Org license, which is the least
#  restrictive of those mentioned above.  See the file COPYING.Xiph in this
#  distribution.

TESTS_ENVIRONMENT = FLAC__TEST_LEVEL=@FLAC__TEST_LEVEL@ FLAC__TEST_WITH_VALRGIND=@FLAC__TEST_WITH_VALGRIND@

SUBDIRS = cuesheets flac-to-flac-metadata-test-files metaflac-test-files pictures

check_SCRIPTS = \
	test_libFLAC.sh \
	test_libFLAC++.sh \
	test_grabbag.sh \
	test_flac.sh \
	test_metaflac.sh \
	test_seeking.sh \
	test_streams.sh

# This one should pass when building out-of-tree (eg 'make distcheck').
check: $(check_SCRIPTS)
	$(srcdir)/test_libFLAC.sh
if FLaC__WITH_CPPLIBS
	$(srcdir)/test_libFLAC++.sh
endif
	$(srcdir)/test_seeking.sh
	$(srcdir)/test_streams.sh
	@echo "----------------"
	@echo "All tests passed"
	@echo "----------------"

# This is the full test suite, but only works correctly in-tree.
# In particular test_grabbag.sh, test_flac.sh and test_metaflac.sh will not
# run correctly out-of-tree.
fullcheck: $(check_SCRIPTS)
	./test_libFLAC.sh
if FLaC__WITH_CPPLIBS
	./test_libFLAC++.sh
endif
	./test_grabbag.sh
	./test_flac.sh
	./test_metaflac.sh
	./test_seeking.sh
	./test_streams.sh
	@echo "----------------"
	@echo "All tests passed"
	@echo "----------------"

EXTRA_DIST = \
	Makefile.lite \
	cuesheet.ok \
	metaflac.flac.in \
	metaflac.flac.ok \
	picture.ok \
	$(check_SCRIPTS) \
	test_wrapper.sh \
	test_bins.sh \
	write_iff.pl

clean-local:
	-rm -f *.raw *.flac *.oga *.ogg *.cmp *.aiff *.wav *.w64 *.rf64 *.diff *.log *.cue core

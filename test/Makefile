# -*- coding: utf-8; -*-
# Emacs Makefile for Tramp

# Copyright (C) 2019 Free Software Foundation, Inc.

# Author: Michael Albinus <michael.albinus@gmx.de>
# Keywords: comm, processes

# This file is free software: you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.

# This file is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with GNU Emacs.  If not, see <http://www.gnu.org/licenses/>.

# This Makefile requires GNU make.

EMACS		= emacs -Q -batch -L ../
CLEAN_FILES	= .\\\#* \\\#* .*~ *~ *.elc *.log
TESTS		= tramp-tests

TRAMP_TEST_ARGS ?=
SELECTOR	?= t

.PHONY: all check test clean distclean

# We want to keep *.elc files.
.SECONDARY:

.SUFFIXES: .elc .el

all: check

check test: $(TESTS)

%-tests: %-tests.elc
	-$(EMACS) -L . -l tramp $(TRAMP_TEST_ARGS) -l $@	\
	--eval '(ert-run-tests-batch-and-exit (quote ${SELECTOR}))'

%.elc: %.el
	$(EMACS) -l bytecomp -f batch-byte-compile $?

clean:
	$(RM) $(CLEAN_FILES)

distclean: clean

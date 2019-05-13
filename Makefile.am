# -*- Makefile -*-

# [[FIXTHIS]] - ACLOCAL_AMFLAGS is evaluted by automake *before* make even runs
# It uses /bin/bash eval to evaluate the line ...
#    so make variables $(...) look like backticks
#    but make variables ${...} look like shell variables with defaults
#
# is a subshell
#    /usr/bin/libtoolize: line 3772: temerarious_flagship_datadir: command not found
#
# these must all be on a single line, no backslash continuations
#ACLOCAL_AMFLAGS = -I m4 -I ${temerarious_flagship_datadir:-/opt/tunitas/share/temerarious-flagship}/ac -I ${hypogeal_twilight_datadir:-/opt/scold/share/hypogeal-twilight}/m4
ACLOCAL_AMFLAGS = -I m4
AUTOMAKE_OPTIONS = no-define subdir-objects foreign

default:
# also configure.ac and HGTW_SUBMODULE_CONFIGURE
# SUBDIRS = @subdirs@
include @temerarious_flagship_datadir@/am/build.mk

# These match with HGTW_WITH_MODULE in configure.ac
DEVELOPMENT_AREAS = \
  $(module_json_prefix) \
  $(module_options_prefix) \
  $(module_nonstd_prefix) \
  $(module_posix_prefix) \
  $(module_std_prefix) \
  $(module_string_prefix) \
  $(module_sys_prefix) \
  $(module_uuid_prefix) \
  $(tunitas_basics_prefix) \
  $(end)
TESTING_AREAS = \
  $(module_cppunit_prefix) \
  $(module_rigging_prefix) \
  $(end)
INSTALLATION_AREAS = \
  $(nonstd_cppunit_prefix) \
  $(nonstd_gcc_prefix) \
  $(nonstd_jsoncpp_prefix) \
  $(nonstd_libhttpserver_prefix) \
  $(std_scold_prefix) \
  $(std_tunitas_prefix) \
  $(end)

default: all

module_SOURCE_SET = $(none)
module_BB_SOURCE_SET = \
  $(warning module_BB_SOURCE_SET is deprecated, instead use module_SOURCE_SET) \
  $(module_SOURCE_SET) \
  $(end)

.PHONY: clean-local mostlyclean-local distclean-local
clean-local mostlyclean-local distclean-local::
clean-dependencies::
clean-local:: clean-dependencies

include src/app/Makefrag.am
include src/app/dump_base64/Makefrag.am
include src/app/dump_iab/Makefrag.am
include src/app/random_base64/Makefrag.am
include src/app/random_iab/Makefrag.am
include src/app/vanity_iab/Makefrag.am
include src/generation/Makefrag.am
include src/tests/unit/Makefrag.am
include src/tunitas/butano/Makefrag.am
include src/tunitas/butano/generation/Makefrag.am
include src/tunitas/butano/tcf/Makefrag.am
include src/want/Makefrag.am

bin_PROGRAMS = \
  bin/dump-base64 \
  bin/dump-iab \
  bin/random-base64 \
  bin/random-iab \
  bin/vanity-iab \
  $(end)
lib_LTLIBRARIES = \
  $(lib_libtunitas_butano_la) \
  $(lib_libtunitas_butano_generation_la) \
  $(lib_libtunitas_butano_tcf_la) \
  $(end)
noinst_LTLIBRARIES = \
  $(lib_libwant_la) \
  $(lib_libgeneration_la) \
  $(lib_libapp_la) \
  $(end)
check_PROGRAMS = \
  $(check_bin_unit) \
  $(end)

include tests/dump-base64/Makefrag.am
include tests/dump-iab/Makefrag.am
include tests/random-base64/Makefrag.am
include tests/random-iab/Makefrag.am
include tests/vanity-iab/Makefrag.am
include tests/unit/Makefrag.am
XFAIL_TESTS = \
  $(tests_unit_XFAIL_TESTS) \
  $(tests_dump_base64_XFAIL_TESTS) \
  $(tests_dump_iab_XFAIL_TESTS) \
  $(tests_random_base64_XFAIL_TESTS) \
  $(tests_random_iab_XFAIL_TESTS) \
  $(tests_vanity_iab_XFAIL_TESTS) \
  $(end)
TESTS = \
  $(tests_unit_TESTS) \
  $(tests_dump_base64_TESTS) \
  $(tests_dump_iab_TESTS) \
  $(tests_random_base64_TESTS) \
  $(tests_random_iab_TESTS) \
  $(tests_vanity_iab_TESTS) \
  $(end)

# --- Mostly boilerplate beyond here
#
# -Wall      ... the language isn't complete without it
# -std=c++1y ... as close to C++14 and beyond as we can get
# -std=c++1z ... as close to C++17 and beyond as we can get
# -ggdb      ... and recall that -ggdb and -O2 don't play well together

Makefile_COMPILER_CPPFLAGS_SET =
Makefile_COMPILER_CFLAGS_SET   = -Wall @CFLAGS_gcc@   @CFLAGS_gdb@
Makefile_COMPILER_CXXFLAGS_SET = -Wall @CXXFLAGS_gcc@ @CXXFLAGS_gdb@
Makefile_COMPILER_LDFLAGS_SET  = -Wall @LDFLAGS_gcc@  @LDFLAGS_gdb@

Makefile_nonstd_PACKAGE_CPPFLAGS_SET = 
Makefile_nonstd_PACKAGE_CFLAGS_SET   = 
Makefile_nonstd_PACKAGE_CXXFLAGS_SET = 
Makefile_nonstd_PACKAGE_LDFLAGS_SET  = 

Makefile_PACKAGE_CPPFLAGS_SET = @CPPFLAGS_jsoncpp@
Makefile_PACKAGE_CFLAGS_SET   =   @CFLAGS_jsoncpp@
Makefile_PACKAGE_CXXFLAGS_SET = @CXXFLAGS_jsoncpp@
Makefile_PACKAGE_LDFLAGS_SET  =  @LDFLAGS_jsoncpp@

Makefile_nonstd_CHECK_CPPFLAGS_SET = 
Makefile_nonstd_CHECK_CFLAGS_SET   = 
Makefile_nonstd_CHECK_CXXFLAGS_SET = 
Makefile_nonstd_CHECK_LDFLAGS_SET  = 

Makefile_CHECK_CPPFLAGS_SET = @CPPFLAGS_cppunit@
Makefile_CHECK_CFLAGS_SET   = @CFLAGS_cppunit@
Makefile_CHECK_CXXFLAGS_SET = @CXXFLAGS_cppunit@
Makefile_CHECK_LDFLAGS_SET  = @LDFLAGS_cppunit@

AM_CPPFLAGS = $(PACKAGE_CPPFLAGS_SET)
AM_CFLAGS   = $(PACKAGE_CFLAGS_SET)
AM_CXXFLAGS = $(PACKAGE_CXXFLAGS_SET)
AM_LDFLAGS  = $(V_LDFLAGS_avoid.VERBOSE_Veq$(V))
AM_LIBTOOLFLAGS = $(V_LIBTOOLFLAGS_VERBOSE_Veq$(V))

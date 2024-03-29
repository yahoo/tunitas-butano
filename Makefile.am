# This is a GNU -*- Makefile -*- fragment that is included by Automake
# Copyright Yahoo Inc, 2021.
# Licensed under the terms of the Apache-2.0 license.
# For terms, see the LICENSE file at https://github.com/yahoo/tunitas-butano/blob/master/LICENSE
# For terms, see the LICENSE file at https://git.tunitas.technology/all/components/butano/tree/LICENSE
#
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
include tests/Makefrag.am
include @temerarious_flagship_datadir@/am/build.am

# also configure.ac and HGTW_SUBMODULE_CONFIGURE
# SUBDIRS = @subdirs@

# These match with HGTW_WITH_MODULE in configure.ac
DEVELOPMENT_AREAS = \
  $(module_cli_core_prefix) \
  $(module_json_prefix) \
  $(module_langu_prefix) \
  $(module_nonstd_prefix) \
  $(module_sys_prefix) \
  $(tunitas_basics_prefix) \
  $(deprecated_DEVELOPMENT_AREAS) \
  $(end)
TESTING_AREAS = \
  $(module_rigging_core_prefix) \
  $(deprecated_TESTING_AREAS) \
  $(end)
INSTALLATION_AREAS = \
  $(nonstd_gcc_prefix) \
  $(nonstd_jsoncpp_prefix) \
  $(std_scold_prefix) \
  $(std_tunitas_prefix) \
  $(deprecated_INSTALLATION_AREAS) \
  $(end)

default: all

.PHONY: clean-local mostlyclean-local distclean-local
clean-local mostlyclean-local distclean-local::
clean-dependencies::
clean-local:: clean-dependencies

include bin/dump-base64.am
include noinst/lib/libapp-dump-base64.am
include bin/dump-iab.am
include noinst/lib/libapp-dump-iab.am
include bin/random-base64.am
include noinst/lib/libapp-random-base64.am
include bin/random-iab.am
include noinst/lib/libapp-random-iab.am

include bin/vanity-iab.am
include noinst/lib/libapp-vanity-iab.am

include noinst/lib/libapp.am
include check/bin/unit.am
include noinst/lib/libwant.am
include noinst/lib/libtunitas-butano.am
include noinst/lib/libtunitas-butano-generation.am
include noinst/lib/libtunitas-butano-tcf.am
include lib/libtunitas-butano.am
include lib/libtunitas-butano-generation.am
include lib/libtunitas-butano-tcf.am

INSTALL_MODULES = \
  $(noinst_lib_libtunitas_butano_la_MODULES) \
  $(noinst_lib_libtunitas_butano_generation_la_MODULES) \
  $(noinst_lib_libtunitas_butano_tcf_la_MODULES) \
  $(noinst_lib_libwant_la_MODULES) \
  $(end)

bin_PROGRAMS = \
  bin/dump-base64 \
  bin/dump-iab \
  bin/random-base64 \
  bin/random-iab \
  bin/vanity-iab \
  $(end)
# WATCHOUT - these installable libraries MUST be in this order to congeal the rpath dependencies upon installation
lib_LTLIBRARIES = \
  lib/libtunitas-butano-tcf.la \
  lib/libtunitas-butano-generation.la \
  $(end)
noinst_LTLIBRARIES = \
  noinst/lib/libwant.la \
  noinst/lib/libapp.la \
  noinst/lib/libapp-vanity-iab.la \
  noinst/lib/libapp-random-iab.la \
  noinst/lib/libapp-random-base64.la \
  noinst/lib/libapp-dump-iab.la \
  noinst/lib/libapp-dump-base64.la \
  noinst/lib/libtunitas-butano-generation.la \
  noinst/lib/libtunitas-butano-tcf.la \
  noinst/lib/libtunitas-butano.la \
  $(end)
check_PROGRAMS = \
  check/bin/unit \
  $(end)

# --- Mostly boilerplate beyond here
#
# -Wall      ... the language isn't complete without it
# -std=c++1y ... as close to C++14 and beyond as we can get
# -std=c++1z ... as close to C++17 and beyond as we can get
# -std=c++2a ... as close to C++20 and beyond as we can get
# -std=c++2b ... as close to C++23 and beyond as we can get
# -std=c++2c ... as close to C++26 and beyond as we can get
# -ggdb      ... and recall that -ggdb and -O2 don't play well together

Makefile_COMPILER_CPPFLAGS_SET =       @CPPFLAGS_gcc@ @CPPFLAGS_gdb@
Makefile_COMPILER_CFLAGS_SET   = -Wall   @CFLAGS_gcc@   @CFLAGS_gdb@
Makefile_COMPILER_CXXFLAGS_SET = -Wall @CXXFLAGS_gcc@ @CXXFLAGS_gdb@
Makefile_COMPILER_LDFLAGS_SET  = -Wall  @LDFLAGS_gcc@  @LDFLAGS_gdb@

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

#                                                  if    did not substitute away                      then use this
#                                                  |           |                                      |            else use the substitution
#                                                  |           |              @CPPFLAGS_no_install@   |            |
#                                                  |           |              |                       |            |
#                                                  |           |              |                       |            |
#                                                  v           v              v                       v            v
Makefile_CHECK_CPPFLAGS_SET = @CPPFLAGS_cppunit@ $(if $(filter %_no_install@, @CPPFLAGS_no_install@), $(empty),    @CPPFLAGS_no_install@)
Makefile_CHECK_CFLAGS_SET   =   @CFLAGS_cppunit@ $(if $(filter %_no_install@, @CFLAGS_no_install@),   $(empty),    @CFLAGS_no_install@)
Makefile_CHECK_CXXFLAGS_SET = @CXXFLAGS_cppunit@ $(if $(filter %_no_install@, @CXXFLAGS_no_install@), $(empty),    @CXXFLAGS_no_install@)
Makefile_CHECK_LDFLAGS_SET  =  @LDFLAGS_cppunit@ $(if $(filter %_no_install@, @LDFLAGS_no_install@),  -no-install, @LDFLAGS_no_install@)

# these are assembled by .../toolflags.mk within temerarious-flagship (hypogeal-twilight) .../toolflags.mk
AM_CPPFLAGS = $(PACKAGE_CPPFLAGS_SET)
AM_CFLAGS   = $(PACKAGE_CFLAGS_SET)
AM_CXXFLAGS = $(PACKAGE_CXXFLAGS_SET)
AM_LDFLAGS  = $(V_LDFLAGS_avoid.VERBOSE_Veq$(V))
AM_LIBTOOLFLAGS = $(V_LIBTOOLFLAGS_VERBOSE_Veq$(V))

deprecated_DEVELOPMENT_AREAS = \
  $(module_cli_prefix) \
  $(module_options_prefix) \
  $(module_posix_prefix) \
  $(module_std_prefix) \
  $(module_string_prefix) \
  $(module_uuid_prefix) \
  $(end)
deprecated_TESTING_AREAS = \
  $(module_cppunit_prefix) \
  $(module_rigging_prefix) \
  $(end)
deprecated_INSTALLATION_AREAS = \
  $(nonstd_cppunit_prefix) \
  $(nonstd_libhttpserver_prefix) \
  $(end)

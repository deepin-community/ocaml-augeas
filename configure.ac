# Augeas
# Copyright (C) 2008-2012 Red Hat Inc., Richard W.M. Jones
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301  USA

dnl Process this file with autoconf to produce a configure script.

AC_CONFIG_MACRO_DIR([m4])

AC_INIT(ocaml-augeas,0.6)

dnl Check for basic C environment.
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_CPP

AC_C_PROTOTYPES
test "x$U" != "x" && AC_MSG_ERROR(Compiler not ANSI compliant)

AC_PROG_CC_C_O

dnl Check for basic OCaml environment & findlib.
AC_PROG_OCAML
AC_PROG_FINDLIB

if test "x$OCAMLFIND" = "x"; then
    AC_MSG_ERROR([You must have ocaml and findlib installed])
fi

dnl Check for libxml2.
PKG_CHECK_MODULES([LIBXML2], [libxml-2.0])

dnl Check for Augeas C library.
PKG_CHECK_MODULES([AUGEAS], [augeas >= 1.2.0])

dnl Check for aug_source function, added in Augeas 1.8.0.
old_LIBS="$LIBS"
LIBS="$AUGEAS_LIBS $LIBS"
AC_CHECK_FUNCS([aug_source])
LIBS="$old_LIBS"

dnl Produce output files.
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_FILES([Makefile META])
AC_OUTPUT

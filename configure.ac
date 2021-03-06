#############################################################################
# xguess
#
# Copyright (C) 1998-2014, David Arnold.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#
#############################################################################

dnl Process this file with autoconf to produce a configure script.
AC_INIT([xguess], [1.5])
AC_CONFIG_SRCDIR([main.c])
AM_INIT_AUTOMAKE

dnl Checks for programs.
AC_PROG_AWK
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_LN_S

dnl Checks for libraries.

# Figure out where X11 lives
AC_PATH_XTRA
if test "$no_x" = yes ; then
    AC_MSG_ERROR("Unable to find the X11 package")
    exit 1
fi

# Add the X11 stuff to the places it belongs
CPPFLAGS="$CPPFLAGS $X_CFLAGS"
LDFLAGS="$LDFLAGS $X_LIBS"
LIBS="$X_PRE_LIBS $X_EXTRA_LIBS $LIBS"

AC_CHECK_HEADERS([X11/XKBlib.h X11/extensions/XKBgeom.h], , , [
    #include <X11/X.h>
    #include <X11/Xlib.h>
    #if HAVE_X11_XKBLIB_H
    # include <X11/XKBlib.h>
    #endif
])

AC_CHECK_LIB(X11, XOpenDisplay)
AC_CHECK_LIB(X11, XkbOpenDisplay)
AC_CHECK_LIB(X11, XkbGetKeyboard)

AC_CHECK_FUNCS(strdup)

AM_CONFIG_HEADER(config.h)
AC_OUTPUT(Makefile)

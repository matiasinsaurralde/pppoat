AC_INIT([pppoat], [dev], [pasis.ua@gmail.com])
AM_INIT_AUTOMAKE([foreign subdir-objects])

AC_CONFIG_FILES([Makefile])

AC_PROG_CC
AM_PROG_CC_C_O

AC_ARG_ENABLE([xmpp], [AS_HELP_STRING([--enable-xmpp], [enable xmpp module])])
AC_ARG_ENABLE([loop], [AS_HELP_STRING([--enable-loop], [enable loop module])])

AC_ARG_WITH([pthreads],
	[AS_HELP_STRING([--without-pthreads], [disable check for pthread.h])])

# check dependencies
if test "x$with_pthreads" != xno; then
  AC_CHECK_LIB(pthread, pthread_create,
	[],
	[AC_MSG_ERROR([pthread support is required])])
fi

if test "x$enable_xmpp" != xno; then
  PKG_CHECK_MODULES([libcouplet], [libcouplet >= 0.8],
	[],
	[AC_MSG_ERROR([libcouplet is required for xmpp module])])

  LIBS="$LIBS $libcouplet_LIBS"
fi

AM_CONDITIONAL([MOD_XMPP], [test "x$enable_xmpp" != xno])
AM_CONDITIONAL([MOD_LOOP], [test "x$enable_loop" = xyes])
AC_OUTPUT

AC_PREREQ(2.52)

AC_INIT([fetch], [1.6], [joerg@NetBSD.org])
dnl AC_INIT([libfetch], [2.0], [joerg@NetBSD.org])

AC_CONFIG_HEADERS(config.h)
AC_CANONICAL_HOST

AC_CHECK_HEADERS([sys/param.h sys/ioctl.h sys/socket.h sys/stat.h sys/time.h])
AC_CHECK_HEADERS([err.h stdint.h termios.h sysexists.h])
AC_CHECK_HEADERS([poll.h sys/poll.h inttypes.h])

AC_TYPE_INTMAX_T

AC_CHECK_FUNCS([getpass getpassphrase setproctitle])
AC_CHECK_LIB([socket], [socket])
AC_CHECK_LIB([crypto], [X509_get_issuer_name])
AC_CHECK_LIB([ssl], [SSL_read])

AS_IF([test "x$ac_cv_lib_crypto_X509_get_issuer_name" = xyes], [
	AS_IF([test "x$ac_cv_lib_ssl_SSL_read" = xyes], [
		AC_DEFINE([WITH_SSL], [], [enable SSL support])
	])
])

AS_CASE([$host],
	[*netbsd*],
		AC_DEFINE([PREFER_GETPASS], [], [getpass supports long passwords]),
	[*linux*|*gnu*|*kfreebsd*],
		AC_DEFINE([_GNU_SOURCE], [], [enable _GNU_SOURCE])
)

AC_DEFINE([INET6], [], [enable INET6])
AC_DEFINE([FTP_COMBINE_CWDS], [], [FTP combine CWDS])

AC_DEFINE([_LARGEFILE_SOURCE], [], [large file source])
AC_DEFINE([_LARGE_FILES], [], [large files])
AC_DEFINE([_FILE_OFFSET_BITS], [64], [file offset bits])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT

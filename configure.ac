AC_PREREQ(2.59)
AC_INIT(jelling, 0.1)
AC_PROG_CC_C99
AC_PROG_SED

AM_INIT_AUTOMAKE([subdir-objects foreign std-options])
AM_SILENT_RULES([yes])
AM_PROG_CC_C_O

PKG_PROG_PKG_CONFIG([0.25])
PKG_CHECK_EXISTS([systemd], [], [AC_MSG_ERROR([systemd not found])])
PKG_CHECK_MODULES([LIBSYSTEMD], [libsystemd >= 221], [],
                  [AC_MSG_ERROR([libsystemd not found])])

AC_ARG_WITH([systemdsystemunitdir],
            AS_HELP_STRING([--with-systemdsystemunitdir=DIR],
                           [Directory for systemd service files]),
            [], [with_systemdsystemunitdir=$($PKG_CONFIG --variable=systemdsystemunitdir systemd)])
AC_SUBST([systemdsystemunitdir], [$with_systemdsystemunitdir])

AC_ARG_WITH([modulesloaddir],
            AS_HELP_STRING([--with-modulesloaddir=DIR],
                           [Directory for systemd module files]),
            [], [with_modulesloaddir=$($PKG_CONFIG --variable=modulesloaddir systemd)])
AC_SUBST([modulesloaddir], [$with_modulesloaddir])

AC_CONFIG_FILES(Makefile)
AC_OUTPUT

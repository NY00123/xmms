# Tell autoconf we're compiling a dynamic dlopen()'d C++ library (also
# called 'plugin' ;) ) using automake and libtool.
AC_INIT(adplug-xmms,1.3)
AC_CONFIG_SRCDIR(src/adplug-xmms.cc)
AC_CONFIG_FILES(Makefile src/Makefile)
AM_INIT_AUTOMAKE
AM_MAINTAINER_MODE
AM_DISABLE_STATIC
AC_LIBTOOL_DLOPEN
AM_PROG_LIBTOOL
AC_LANG(C++)

# Check if we got a sane C/C++ compilation environment.
AC_PROG_INSTALL
AC_PROG_CC
AC_PROG_CXX

# Check library/program dependencies.
ACX_PTHREAD(,AC_MSG_ERROR([*** POSIX threads not installed ***]))
PKG_CHECK_MODULES([adplug], [adplug >= 2.2])
AM_PATH_XMMS(0.9.5.1,,AC_MSG_ERROR([*** XMMS >= 0.9.5.1 not installed ***]))

# Determine plugin installation directory
if test x${adplug_distcheck} == xyes; then
   xmms_input_plugin_dir=${libdir}
fi

if test x${xmms_input_plugin_dir} == x; then
   xmms_input_plugin_dir=${XMMS_INPUT_PLUGIN_DIR}
else
   echo "Installing to user-specified directory: ${xmms_input_plugin_dir}"
fi

AC_SUBST(xmms_input_plugin_dir)

# Enable debug logging on user request
AC_ARG_ENABLE([debug],AC_HELP_STRING([--enable-debug],
[Compile with debug logging support (default is to disable debug logging)]),
	AC_DEFINE(DEBUG))

AC_OUTPUT

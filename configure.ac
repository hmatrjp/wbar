dnl make yadickson soto

AC_INIT([wbar],[2.4.3])
AM_INIT_AUTOMAKE([ filename-length-max=256 tar-ustar subdir-objects ])

AC_CONFIG_HEADERS(config.h)

AC_PROG_CXX
AC_PROG_INSTALL


eval "prefix=$prefix"

if test "$prefix" = "NONE" ; then
    eval "prefix=/usr"
fi

eval "exec_prefix=$prefix"
eval "libdir=$libdir"
eval "bindir=$bindir"
eval "datadir=$datadir"
eval "localedir=$localedir"
eval "sysconfdir=$sysconfdir"

LIBDIR=`eval echo $libdir`
BINDIR=`eval echo $bindir`
SHARE_DATADIR=`eval echo $datadir`
LOCALEDIR=`eval echo $localedir`
SYSCONFDIR=`eval echo $sysconfdir`

AC_SUBST(LIBDIR)
AC_SUBST(BINDIR)
AC_SUBST(SYSCONFDIR)

AC_SUBST(GETTEXT_PACKAGE, [AC_PACKAGE_NAME])
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE, "$GETTEXT_PACKAGE" , [ The gettext package ])

AC_SUBST(GNOMELOCALEDIR, $LOCALEDIR)
AC_DEFINE_UNQUOTED(GNOMELOCALEDIR, "$GNOMELOCALEDIR" , [ The gettext package dir ])

AC_SUBST(DEFAULT_CONFIGDIR, "$SYSCONFDIR/AC_PACKAGE_NAME.d")
AC_DEFINE_UNQUOTED(DEFAULT_CONFIGDIR, "$DEFAULT_CONFIGDIR" , [ The default config dir ])

AC_SUBST(AUTOSTARTDIR, "$SYSCONFDIR/xdg/autostart")
AC_DEFINE_UNQUOTED(AUTOSTARTDIR, "$AUTOSTARTDIR" , [ The autostart dir ])

AC_SUBST(PIXMAPDIR, "$SHARE_DATADIR/pixmaps")
AC_DEFINE_UNQUOTED(PIXMAPDIR, "$PIXMAPDIR" , [ The pixmaps dir ])

AC_SUBST(UIXML_DIR, "$SHARE_DATADIR/AC_PACKAGE_NAME")
AC_DEFINE_UNQUOTED(UIXML_DIR, "$UIXML_DIR" , [ The UI XML dir ])

AC_SUBST(UIXML_NAME, "$UIXML_DIR/AC_PACKAGE_NAME.ui")
AC_DEFINE_UNQUOTED(UIXML_NAME, "$UIXML_NAME" , [ The GtkBuilder UI filename ])

AC_SUBST(DEFAULT_ARGV, "--bpress --above-desk --vbar --pos right --isize 64 --idist 5 --nanim 4 --falfa 65")
AC_DEFINE_UNQUOTED(DEFAULT_ARGV, "$DEFAULT_ARGV" , [ The default argv ])

IT_PROG_INTLTOOL()
AM_GNU_GETTEXT([external])
AM_GNU_GETTEXT_VERSION([0.19])
PKG_PROG_PKG_CONFIG

PKG_CHECK_MODULES(modules, [imlib2 x11 xrandr])
AC_SUBST(modules_CFLAGS)
AC_SUBST(modules_LIBS)

AC_ARG_ENABLE(wbar-config, AS_HELP_STRING([--disable-wbar-config],
	[build without the GTK+ configuration interface]),[use_wbar_config=$enableval],
	[use_wbar_config=yes])
if test "$use_wbar_config" = "yes"; then
	PKG_CHECK_MODULES(gui_modules, [gtk+-3.0])
	AC_SUBST(gui_modules_CFLAGS)
	AC_SUBST(gui_modules_LIBS)
fi

AM_CONDITIONAL([WBAR_CONFIG],[test "$use_wbar_config" = "yes"])

AC_PATH_PROG(PIDOF_BIN, pidof, pgrep)
AC_DEFINE_UNQUOTED(PIDOF_BIN, "$PIDOF_BIN ", [ program to retreive wbar pid ])

AC_CONFIG_FILES([Makefile \
share/Makefile \
etc/Makefile \
etc/wbar.cfg \
etc/wbar.desktop.in \
pixmaps/Makefile \
po/Makefile.in \
doc/Makefile
doc/man/Makefile
doc/man/es/Makefile
src/Makefile])

AC_OUTPUT



lib_LTLIBRARIES = libXau.la

AM_CFLAGS = $(XAU_CFLAGS)

INCLUDES = -I${top_srcdir}/include

libXau_la_LDFLAGS = -version-number 6:0:0 -no-undefined

libXau_la_LIBADD = $(XAU_LIBS)

libXau_la_SOURCES = \
	AuDispose.c \
	AuFileName.c \
	AuGetAddr.c \
	AuGetBest.c \
	AuLock.c \
	AuRead.c \
	AuUnlock.c \
	AuWrite.c

if KERBEROS
libXau_la_SOURCES +=k5encode.c
endif KERBEROS

xauincludedir=$(includedir)/X11

xauinclude_HEADERS = include/X11/Xauth.h

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = xau.pc

check_PROGRAMS=Autest
TESTS=Autest

Autest_SOURCES=Autest.c
Autest_LDADD=libXau.la

LIB_MAN_DIR_SUFFIX = $(LIB_MAN_DIR:@mandir@/man%=%)

libmandir = $(LIB_MAN_DIR)
libman_PRE = Xau.man
BUILT_SOURCES = shadows.DONE
CLEANFILES = $(libman_DATA) $(BUILT_SOURCES)
libman_DATA = $(libman_PRE:man=@LIB_MAN_SUFFIX@) \
	      $(Xau_shadows:=.@LIB_MAN_SUFFIX@)

EXTRA_DIST = xau.pc.in $(libman_PRE)

Xau_shadows =                               \
    XauFileName                             \
    XauReadAuth                             \
    XauLockAuth                             \
    XauUnlockAuth                           \
    XauWriteAuth                            \
    XauDisposeAuth                          \
    XauGetAuthByAddr                        \
    XauGetBestAuthByAddr

shadows.DONE:
	-rm -f $(Xau_shadows:=.@LIB_MAN_SUFFIX@)
	(for i in $(Xau_shadows:=.@LIB_MAN_SUFFIX@) ; do \
	 echo .so man$(LIB_MAN_DIR_SUFFIX)/Xau.$(LIB_MAN_SUFFIX) > $$i; \
	 done)
	touch shadows.DONE

XORGRELSTRING = @PACKAGE_STRING@
  XORGMANNAME = X Version 11

Xau.$(LIB_MAN_SUFFIX): $(srcdir)/Xau.man
	sed 's/__xorgversion__/"$(XORGRELSTRING)" "$(XORGMANNAME)"/' \
	< $(srcdir)/Xau.man > Xau.$(LIB_MAN_SUFFIX)

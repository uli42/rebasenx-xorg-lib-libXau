lib_LTLIBRARIES = libXau.la

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

xauinclude_HEADERS = Xauth.h

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = xau.pc

man_MANS = Xau.3

EXTRA_DIST = xau.pc.in Autest.c $(man_MANS)

#	$NetBSD: Makefile,v 1.1.1.1 2016/06/10 03:42:14 mrg Exp $

.include <bsd.own.mk>

PROG=	xorgconfig

.PATH:	${X11SRCDIR.xorg-server}/hw/xfree86/utils/xorgconfig

SRCS=	xorgconfig.c cards.c

LDADD=	-lxkbfile -lXext -lX11
DPADD=	${LIBXKBFILE} ${LIBXEXT} ${LIBX11}

CPPFLAGS+=	-DCARD_DATABASE_FILE='"${X11USRLIBDIR}/X11/Cards"' \
		-DXKB_RULES_DIR=\"${X11USRLIBDIR}/X11/xkb/rules\" \
		-DXVERSION=${XORG_VERSION_CURRENT} \
		-DWSCONS_SUPPORT -D__XKBDEFRULES__='"xorg"' \
		-D__XCONFIGFILE__='"xorg.conf"' \
		-D__XSERVERNAME__='"Xorg"' \
		-D__XKBDEFRULES__='"xorg"' \
		-DXVENDORNAME='"The X.Org Foundation"' \
		-DFILEMANSUFFIX=\"5\" \
		-DXVERSIONSTRING=\"1.4.2\"

.if ${MACHINE_ARCH} == "i386" || ${MACHINE} == "cats" || ${MACHINE} == "ofppc"
CPPFLAGS+=	-DPCVT_SUPPORT
.endif

FILES+=		Cards
FILESDIR_Cards=	${X11USRLIBDIR}/X11

.include <bsd.x11.mk>
.include <bsd.prog.mk>
